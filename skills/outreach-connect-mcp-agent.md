---
name: Connect an agent to the Outreach MCP server
description: Wire an MCP client to Outreach over OAuth 2.1 with Dynamic Client Registration, and know which of the 41 tools are safe to auto-approve and where the tool surface stops.
api: mcp/outreach-mcp.yml
generated: '2026-08-13'
method: generated
source: https://developers.outreach.io/mcp-server + probed https://api.outreach.io/.well-known/oauth-protected-resource
endpoint: https://api.outreach.io/mcp
transport: streamable-http
tools:
  - current_user
  - prospect_search
  - prospect_create
  - sequence_search
  - sequence_add_prospects
  - account_answer_question
  - input_fields_fetch
---

# Connect an agent to the Outreach MCP server

## Endpoint

```
https://api.outreach.io/mcp
```

Outreach's documentation does not print this URL — the getting-started checklist tells you to obtain it from
Outreach. It is discoverable without asking: `GET https://api.outreach.io/.well-known/oauth-protected-resource`
returns `{"resource":"https://api.outreach.io/mcp", ...}`. `mcp.outreach.io` does not exist.

Transport is **streamable HTTP**. MCP revision **2025-03-26 and above**.

## Authorize

Outreach uses OAuth 2.1 + PKCE with **Dynamic Client Registration** (RFC 7591), so no admin has to register
your client first.

1. Fetch `https://api.outreach.io/.well-known/oauth-authorization-server`.
2. `POST` to `https://api.outreach.io/mcpOAuth/register` to get a `client_id`.
3. Authorization code + PKCE (`S256`) at `https://api.outreach.io/mcpOAuth/authorize`.
4. Exchange at `https://api.outreach.io/mcpOAuth/token` (`client_secret_post`).
5. Send the bearer token on every tool call.

An unauthenticated call returns `401` with
`WWW-Authenticate: Bearer resource_metadata="https://api.outreach.io/.well-known/oauth-protected-resource"` —
a well-behaved MCP client follows that automatically.

The authorization-server metadata advertises `scopes_supported: ["prospects.all"]`. That is narrower than
the tool surface, which reaches accounts, opportunities, sequences, tasks, teams, users and Kaia. Do not
assume the advertised scope list is the effective grant.

## Discover, do not hardcode

Call `tools/list`. Tool schemas are self-describing and Outreach says they change between releases. Do not
pin a field list.

For per-org schema (custom fields, required validations), the agent should call `input_fields_fetch`,
`filter_fields_fetch` and `filter_schema_fetch` before constructing a create or a filter.

## Permission model

Permissions inherit from the authenticated Outreach user's RBAC profile. If the user cannot delete an
opportunity in the UI, the agent cannot either. Tool calls are attributed to that user in Outreach's
activity history, and disabling the user at the IDP revokes access immediately.

## Auto-approve rules

- **27 read tools** are `readOnlyHint: true`, `destructiveHint: false`, `idempotentHint: true` — safe to
  auto-approve and safe to retry.
- **11 write tools** are `idempotentHint: false`. Retrying `prospect_create` makes a second prospect. Gate
  them.
- **4 tools are `destructiveHint: true`**: `account_delete`, `opportunity_delete`, `prospect_delete`,
  `sequence_states_destroy`. Always confirm with a human.
- `account_answer_question` and `opportunity_answer_question` are marked **write** — not because they mutate
  a record you asked about, but because the question itself is persisted to the account/prospect Q&A chat
  history in the Outreach web app. Treat them as writes for audit purposes.

Two caveats on the published annotations: Outreach's Tool Catalog says all tools advertise
`openWorldHint: false` while its Tool Annotations page says `openWorldHint: true`, and the tool count is
given as 41 on one page and 32 on two others. Trust `tools/list`, not the docs.

## Working patterns

```
account_search -> account_get_by_id -> account_answer_question       # explore
prospect_create -> sequence_search -> sequence_add_prospects         # onboard
input_fields_fetch -> prospect_create                                # org-specific fields
sequence_state_search -> sequence_states_destroy                     # unenroll (confirm first)
```

Batch where the tool allows it — `sequence_add_prospects` takes multiple prospect ids. Do not build polling
loops on batch tools; check state once and use REST webhooks for long-running work.

## Where the tool surface stops

MCP is a narrow projection of the REST API — roughly one operation in eight has a tool. There is **no** MCP
tool for: completing/snoozing/advancing a task, activating or pausing a sequence, any of the 27 bulk batch
actions, the CSV import pipeline, mailbox management, webhook management, audit logs, compliance requests,
notes, snippets, templates, products or purchases. For those, fall back to the REST API at
`https://api.outreach.io/api/v2` — see `mcp/outreach-tool-crosswalk.yml` for the full divergence.

## References

- mcp/outreach-mcp.yml — endpoint, OAuth metadata, full tool catalog with annotations
- mcp/outreach-tool-crosswalk.yml — every tool bound to its REST operation, plus MCP-only and REST-only gaps
- authentication/outreach-authentication.yml
