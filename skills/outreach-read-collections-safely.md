---
name: Read Outreach collections safely at scale
description: Page, filter, sort and trim JSON:API collections in Outreach without blowing the hourly rate limit or tripping the deprecated count/offset behaviours.
api: openapi/outreach-openapi.yml
generated: '2026-08-13'
method: generated
source: https://developers.outreach.io/api/making-requests
operations:
  - GET /prospects
  - GET /accounts
  - GET /opportunities
  - GET /tasks
  - GET /mailings
  - GET /sequenceStates
scopes:
  - prospects.read
  - accounts.read
  - opportunities.read
  - tasks.read
mcp_equivalent:
  - prospect_search
  - account_search
  - opportunity_search
  - task_search
---

# Read Outreach collections safely at scale

Base URL: `https://api.outreach.io/api/v2`. Every collection endpoint behaves identically — the rules below
apply to `/prospects`, `/accounts`, `/opportunities`, `/tasks`, `/mailings`, `/sequenceStates` and the rest.

## Budget first

- **10,000 requests per hour, per user.** Not per app, per user.
- Kaia recordings and transcripts are far tighter: **3 calls/second and 6,000 calls/day, per org**.
- Read `X-RateLimit-Limit`, `X-RateLimit-Remaining` and `X-RateLimit-Reset` off every response and stop
  before you hit zero. `429` returns `errors[0].id = rateLimitExceeded`.
- Your subscription also carries an annual API-call entitlement (250,000 to 1,000,000 depending on the
  Amplify tier). Staying under the hourly rate limit does not keep you under that.

## Page with cursors, not offsets

```
GET /prospects?page[size]=50&count=false
```

Follow `links.next` from the response body. Do not construct cursors yourself — they are opaque.

Offset pagination still works but is deprecated and is a performance trap: max offset **10,000**, max
`page[limit]` **1,000**, default page size **50**.

## Do not count unless you need the number

Counting is the most expensive part of a collection query. Pass `count=false` unless you genuinely need
`meta.count`.

If you do need it, know that it lies under two conditions:

- over 2,000,000 matches: `{"count":2000000,"count_truncated":true}`
- under system load: `{"count":0,"count_truncated":true}`

Always check `count_truncated` before treating `count` as a total.

Applications registered after 2024-10-13 default to `count=false` — if your integration expects
`meta.count`, pass `count=true` explicitly.

## Filter precisely

```
GET /prospects?filter[firstName]=Sally
GET /prospects?filter[id]=1,2,3,5,8,13
GET /prospects?filter[id]=5..10
GET /prospects?filter[updatedAt]=2017-01-01..inf
GET /accounts?filter[buyerIntentScore]=__null__
```

When a value contains a literal comma or `..`, switch syntax:

```
GET /prospects?newFilterSyntax=true&filter[firstName][]=Sally&filter[firstName][]=Katie
GET /prospects?newFilterSyntax=true&filter[id][gte]=5&filter[id][lte]=10
```

**Relationship filters are id-only.** `filter[account][name]=Acme` was deprecated in May 2023. Do it in two
steps:

```
GET /accounts?filter[name]=Acme&fields[account]=            -> ids
GET /prospects?filter[account][id]=1,2,3
```

`filter[q]=` prefix search exists but only on Accounts and Prospects.

## Trim the payload

```
GET /prospects/1?include=account,stage&fields[prospect]=firstName,lastName&fields[account]=name&fields[stage]=name
```

`fields[...]` is keyed by resource **type**, not relationship name — `owner` is a `user`, so it is
`fields[user]`. Sparse fieldsets are the single biggest lever on both latency and your call budget.

Note the 2026-10-01 change: `contactHistogram` leaves the default Prospect payload. If you need it, request
it — and remember that naming `fields[prospect]` at all means you get **only** what you name.

## Sort

```
GET /prospects?sort=lastName,-firstName
```

Sorting by a relationship's attribute is deprecated. Include the attribute and sort client-side.

## Incremental sync pattern

```
GET /prospects?filter[updatedAt]=2026-08-01T00:00:00..inf&sort=updatedAt&page[size]=50&count=false
```

Walk `links.next`, keep the highest `updatedAt` you saw as your next watermark, and subscribe to webhooks
(`POST /webhooks`) so you only poll for the gaps.

## References

- conventions/outreach-conventions.yml
- rate-limits/outreach-rate-limits.yml
- lifecycle/outreach-lifecycle.yml — the dated deprecations that change these behaviours
