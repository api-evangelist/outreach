---
name: Subscribe to Outreach webhooks
description: Register an Outreach webhook, verify its HMAC signature, and survive the retry, suspension and deactivation rules that will silently kill a subscription.
api: openapi/outreach-openapi.yml
generated: '2026-08-13'
method: generated
source: https://developers.outreach.io/api/webhooks
operations:
  - POST /webhooks
  - GET /webhooks
  - GET /webhooks/{id}
  - PATCH /webhooks/{id}
  - DELETE /webhooks/{id}
scopes:
  - webhooks.all
event_surface: webhooks/outreach-webhooks-asyncapi.yml
---

# Subscribe to Outreach webhooks

Base URL: `https://api.outreach.io/api/v2`. The full channel and payload catalogue is in
`webhooks/outreach-webhooks-asyncapi.yml`.

## 1. Register the subscription

```
POST /webhooks
{"data":{"type":"webhook","attributes":{
  "url":"https://example.com/outreach/webhook",
  "resource":"prospect",
  "action":"created",
  "secret":"<your-shared-secret>",
  "payloadVersion":"v2"}}}
```

- One subscription = **one `resource` + `action` pair**. `*` is accepted as a wildcard on either field.
- The endpoint must be HTTPS.
- Supply a `secret` at creation. Without it, deliveries arrive unsigned and you cannot tell a real Outreach
  call from anyone who learned your URL.
- Payload version 1 carries only changed attributes. Version 2 additionally carries a `beforeUpdate`
  envelope with the prior values — use v2 unless you have a reason not to.

Covered resources include account, call, contact, email address, import, Kaia recording, mailing,
opportunity, opportunity prospect role, prospect, sequence, sequence state, task and user.

## 2. Verify every delivery

Each delivery carries `Outreach-Webhook-Signature`: the HMAC hex digest of your secret over the **raw**
request body. Compute it over the bytes you received, before any JSON parsing or re-serialisation, and
compare in constant time. Reject anything that does not match — do not process it, do not log the body.

Each delivery also carries `outreach-webhook-cleanup-token`, which lets you deregister the subscription even
after your API access has been revoked. Store it with the subscription; it is your only exit if the OAuth
grant disappears.

## 3. Respond correctly, or lose the subscription

The delivery contract is unusually unforgiving and worth restating exactly:

- Respond **200 within 5 seconds**. Acknowledge first, process asynchronously.
- On a **network failure** Outreach retries up to 3 times (4 attempts total) at 1-second intervals.
- A **non-2xx response — including 500 and 429 — is treated as an acknowledgment and is NOT retried.** If
  your handler is overloaded and returns 429, that event is gone. This is the opposite of most webhook
  systems; design for it.
- Redirects are **not** followed.
- A hostname resolving to a private IP range **suspends** the webhook for 1 hour. A DNS failure suspends it
  for 1 minute.
- A webhook that stays unrecovered for **7+ days is permanently deactivated**.

Monitor `GET /webhooks` for subscriptions that have gone inactive; nothing will tell you otherwise.

## 4. Payload shape

Deliveries are JSON:API-shaped — `data.type`, `data.id`, `data.attributes` with the changed attributes
only, and (on payload version 2) the `beforeUpdate` envelope. Treat attribute absence as "unchanged", not
as "null".

## 5. Manage the subscription

```
GET    /webhooks
GET    /webhooks/{id}
PATCH  /webhooks/{id}
DELETE /webhooks/{id}
```

## References

- webhooks/outreach-webhooks-asyncapi.yml — every channel and message
- errors/outreach-error-codes.yml
- authentication/outreach-authentication.yml
