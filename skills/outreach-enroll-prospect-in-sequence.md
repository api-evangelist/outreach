---
name: Enroll a prospect in an Outreach sequence
description: Create an account and prospect in Outreach, find the right sequence, and enroll the prospect — the core outbound motion, done correctly against the JSON:API contract.
api: openapi/outreach-openapi.yml
generated: '2026-08-13'
method: generated
source: openapi/_original/outreach-openapi.json + https://developers.outreach.io/api/common-patterns
operations:
  - POST /accounts
  - POST /prospects
  - GET /sequences
  - POST /sequenceStates
  - GET /sequenceStates
scopes:
  - accounts.write
  - prospects.write
  - sequences.read
  - sequenceStates.all
mcp_equivalent:
  - prospect_create
  - sequence_search
  - sequence_add_prospects
  - sequence_state_search
---

# Enroll a prospect in an Outreach sequence

Base URL: `https://api.outreach.io/api/v2`

## Before you call anything

- Every request needs **both** headers. Missing the media type returns `415` / `unsupportedMediaType`:
  - `Authorization: Bearer <access_token>`
  - `Content-Type: application/vnd.api+json`
- Access tokens live **2 hours**. Cache them. Minting a token for the same user more than once per 60
  seconds returns `429`.
- Outreach has **no idempotency key**. Retrying a `POST` creates a second record. Before retrying a failed
  create, re-query the collection to check whether the first attempt landed.

## 1. Create the account first

You cannot write to an account's `prospects` relationship — the relationship is writable from the prospect
side only. So the account has to exist first.

```
POST /accounts
{"data":{"type":"account","attributes":{"name":"Acme"}}}
```

`201` returns the account with its `id`. `422` / `validationError` means a field failed validation; read
`errors[0].source.pointer` for the offending attribute.

If the account may already exist, look before you leap:

```
GET /accounts?filter[name]=Acme&count=false
```

## 2. Create the prospect against that account

```
POST /prospects
{"data":{"type":"prospect",
         "attributes":{"firstName":"Sally","lastName":"Smith","emails":["sally@example.com"],"title":"CEO"},
         "relationships":{"account":{"data":{"type":"account","id":1}}}}}
```

Do **not** add `?include=account` to a create — including related objects on create/update was removed in
May 2023. If you need the account back, issue a follow-up `GET /prospects/{id}?include=account`.

## 3. Resolve the sequence by name

```
GET /sequences?filter[name]=Executive%20Outbound%20Touch&fields[sequence]=name&count=false
```

Take `data[0].id`. If the collection is empty the sequence name is wrong or the user cannot see it — do not
create a sequence as a fallback.

## 4. Enroll

```
POST /sequenceStates
{"data":{"type":"sequenceState",
         "relationships":{"prospect":{"data":{"type":"prospect","id":2}},
                          "sequence":{"data":{"type":"sequence","id":7}},
                          "mailbox":{"data":{"type":"mailbox","id":3}}}}}
```

A mailbox is normally required for an email sequence — resolve it with `GET /mailboxes` for the sending
user. `422` here usually means the prospect is already active in that sequence, or has no deliverable email
address.

For many prospects at once use the bulk action instead of a loop:

```
POST /batches/actions/prospectsAddToSequence?actionParams[filter][id][]=2&actionParams[filter][id][]=3
```

Poll `GET /batches/{id}` for state, and `POST /batches/{id}/actions/confirm` if the batch requires
confirmation. Never loop single writes when a batch action exists — you have 10,000 requests per hour per
user.

## 5. Verify

```
GET /sequenceStates?filter[prospect][id]=2&filter[sequence][id]=7&count=false
```

Filter by relationship **id** only. Filtering by a relationship's other attributes was deprecated in May
2023; resolve ids first, then filter.

## Errors you will actually hit

| Status | `errors[0].id` | What to do |
|---|---|---|
| 403 | `unauthorizedOauthScope` | Re-authorize with the missing scope. Scopes are not additive. |
| 403 | `unauthorizedRequest` | The token has the scope; the user's governance profile forbids the action. Escalate to an Outreach admin, do not retry. |
| 404 | `resourceNotFound` | Wrong id, or the record is invisible to this user. |
| 415 | `unsupportedMediaType` | You forgot `Content-Type: application/vnd.api+json`. |
| 422 | `validationError` | Read `source.pointer`. Fix the field. Retrying unchanged will fail identically. |
| 429 | `rateLimitExceeded` | Back off until `X-RateLimit-Reset` / `Retry-After`. |
| 503 | `scheduledServerMaintenance` | Maintenance window; retry after the `Retry-After` timestamp. |

## References

- conventions/outreach-conventions.yml — pagination, filtering, sparse fieldsets, write semantics
- errors/outreach-error-codes.yml — the full published error catalog
- scopes/outreach-scopes.yml — scope grammar and the published scope list
