# Outreach

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Outreach is a sales execution and revenue platform for go-to-market teams, unifying email, calling, social and meetings into sequenced outbound motions with AI agents layered on top. Its public developer surface is a JSON API 1.0 REST API at api.outreach.io/api/v2 covering accounts, prospects, opportunities, sequences, sequence states, mailings, calls, tasks, teams, users, imports and webhooks across 51 tagged resources and 253 operations, authorized by OAuth 2.0 with a scope-per-resource permission model and a separate server-to-server JWT token for unattended integrations. Outreach also runs a remote Model Context Protocol server at api.outreach.io/mcp with 41 tools, authorized by OAuth 2.1 with PKCE and Dynamic Client Registration, plus a client extensibility SDK for embedding web widgets inside the Outreach app, an event-driven webhook surface with HMAC-signed deliveries, and Outreach Data Sharing over Snowflake and Delta Sharing.

**Areas:** Sales · Sales Engagement · Sequences · CRM · Email · Revenue Operations · Sales Execution · Prospecting · Agents · MCP · Outreach

## Outreach on APIs.io

Everything profiled for Outreach is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/outreach/](https://apis.io/providers/outreach/)** — or go straight to one of the APIs or properties below.

### APIs (55)

- [Outreach MCP Server](https://apis.io/apis/outreach/outreach-mcp-server/) — Remote Model Context Protocol server exposing Outreach as 41 agent tools (27 read, 11 write, 3 schema introspection) over streamable HTTP, authorized by…
- [Outreach Client Extensions API](https://apis.io/apis/outreach/outreach-client-extensions-api/) — Client extensibility surface for embedding a web application inside the Outreach client — shell, tab and tile web-widget extensions, a text-editor…
- [Outreach Data Sharing](https://apis.io/apis/outreach/outreach-data-sharing/) — Read-only access to an organization's Outreach data through Snowflake secure data sharing and Delta Sharing, in a ready-to-query format with no data copy or…
- [Outreach Webhooks](https://apis.io/apis/outreach/outreach-webhooks/) — Event-driven webhook deliveries for accounts, calls, contacts, email addresses, imports, Kaia recordings, mailings, opportunities, opportunity prospect…
- [Outreach Account API](https://apis.io/apis/outreach/outreach-account-api/) — <SchemaDefinition schemaRef="#/components/schemas/account" /> ## Account Relationships <SchemaDefinition…
- [Outreach Account Note API](https://apis.io/apis/outreach/outreach-account-note-api/) — <SchemaDefinition schemaRef="#/components/schemas/accountNote" /> ## Account Note Relationships <SchemaDefinition…
- [Outreach Audit Log API](https://apis.io/apis/outreach/outreach-audit-log-api/) — <SchemaDefinition schemaRef="#/components/schemas/auditLog" /> ## Audit Log Custom Filters | **NAME**| **VALUE TYPE** | **VALUE KIND** | **VALUE LENGTH** |…
- [Outreach Batch API](https://apis.io/apis/outreach/outreach-batch-api/) — <SchemaDefinition schemaRef="#/components/schemas/batch" /> ## Batch Relationships <SchemaDefinition schemaRef="#/components/schemas/batchRelationships" />…
- [Outreach Batch Item API](https://apis.io/apis/outreach/outreach-batch-item-api/) — <SchemaDefinition schemaRef="#/components/schemas/batchItem" /> ## Batch Item Relationships <SchemaDefinition…
- [Outreach Call API](https://apis.io/apis/outreach/outreach-call-api/) — <SchemaDefinition schemaRef="#/components/schemas/call" /> ## Call Relationships <SchemaDefinition schemaRef="#/components/schemas/callRelationships" /> ##…
- [Outreach Call Disposition API](https://apis.io/apis/outreach/outreach-call-disposition-api/) — <SchemaDefinition schemaRef="#/components/schemas/callDisposition" /> ## Call Disposition Relationships <SchemaDefinition…
- [Outreach Call Purpose API](https://apis.io/apis/outreach/outreach-call-purpose-api/) — <SchemaDefinition schemaRef="#/components/schemas/callPurpose" /> ## Call Purpose Relationships <SchemaDefinition…
- [Outreach Compliance Request API](https://apis.io/apis/outreach/outreach-compliance-request-api/) — <SchemaDefinition schemaRef="#/components/schemas/complianceRequest" /> ## Compliance Request Relationships <SchemaDefinition…
- [Outreach Content Category API](https://apis.io/apis/outreach/outreach-content-category-api/) — <SchemaDefinition schemaRef="#/components/schemas/contentCategory" /> ## Content Category Relationships <SchemaDefinition…
- [Outreach Content Category Membership API](https://apis.io/apis/outreach/outreach-content-category-membership-api/) — <SchemaDefinition schemaRef="#/components/schemas/contentCategoryMembership" /> ## Content Category Membership Relationships <SchemaDefinition…
- [Outreach Content Category Ownership API](https://apis.io/apis/outreach/outreach-content-category-ownership-api/) — <SchemaDefinition schemaRef="#/components/schemas/contentCategoryOwnership" /> ## Content Category Ownership Relationships <SchemaDefinition…
- [Outreach Custom Duty API](https://apis.io/apis/outreach/outreach-custom-duty-api/) — <SchemaDefinition schemaRef="#/components/schemas/customDuty" /> ## ⌵ Custom Duty Actions
- [Outreach Duty API](https://apis.io/apis/outreach/outreach-duty-api/) — <SchemaDefinition schemaRef="#/components/schemas/duty" /> ## ⌵ Duty Actions
- [Outreach Email Address API](https://apis.io/apis/outreach/outreach-email-address-api/) — <SchemaDefinition schemaRef="#/components/schemas/emailAddress" /> ## Email Address Relationships <SchemaDefinition…
- [Outreach Event API](https://apis.io/apis/outreach/outreach-event-api/) — <SchemaDefinition schemaRef="#/components/schemas/event" /> ## Event Relationships <SchemaDefinition schemaRef="#/components/schemas/eventRelationships" />…
- [Outreach Favorite API](https://apis.io/apis/outreach/outreach-favorite-api/) — <SchemaDefinition schemaRef="#/components/schemas/favorite" /> ## Favorite Relationships <SchemaDefinition…
- [Outreach Import API](https://apis.io/apis/outreach/outreach-import-api/) — <SchemaDefinition schemaRef="#/components/schemas/import" /> ## Import Relationships <SchemaDefinition schemaRef="#/components/schemas/importRelationships"…
- [Outreach Kaia Recording API](https://apis.io/apis/outreach/outreach-kaia-recording-api/) — <SchemaDefinition schemaRef="#/components/schemas/kaiaRecording" /> ## Kaia Recording Relationships <SchemaDefinition…
- [Outreach Kaia Voice Import API](https://apis.io/apis/outreach/outreach-kaia-voice-import-api/) — <SchemaDefinition schemaRef="#/components/schemas/kaiaVoiceImport" /> ## ⌵ Kaia Voice Import Actions
- [Outreach Mail Alias API](https://apis.io/apis/outreach/outreach-mail-alias-api/) — <SchemaDefinition schemaRef="#/components/schemas/mailAlias" /> ## Mail Alias Relationships <SchemaDefinition…
- [Outreach Mailbox API](https://apis.io/apis/outreach/outreach-mailbox-api/) — <SchemaDefinition schemaRef="#/components/schemas/mailbox" /> ## Mailbox Relationships <SchemaDefinition…
- [Outreach Mailing API](https://apis.io/apis/outreach/outreach-mailing-api/) — <SchemaDefinition schemaRef="#/components/schemas/mailing" /> ## Mailing Relationships <SchemaDefinition…
- [Outreach Opportunity API](https://apis.io/apis/outreach/outreach-opportunity-api/) — <SchemaDefinition schemaRef="#/components/schemas/opportunity" /> ## Opportunity Relationships <SchemaDefinition…
- [Outreach Opportunity Prospect Role API](https://apis.io/apis/outreach/outreach-opportunity-prospect-role-api/) — <SchemaDefinition schemaRef="#/components/schemas/opportunityProspectRole" /> ## Opportunity Prospect Role Relationships <SchemaDefinition…
- [Outreach Opportunity Stage API](https://apis.io/apis/outreach/outreach-opportunity-stage-api/) — <SchemaDefinition schemaRef="#/components/schemas/opportunityStage" /> ## Opportunity Stage Relationships <SchemaDefinition…
- [Outreach Org Setting API](https://apis.io/apis/outreach/outreach-org-setting-api/) — <SchemaDefinition schemaRef="#/components/schemas/orgSetting" /> ## ⌵ Org Setting Actions
- [Outreach Persona API](https://apis.io/apis/outreach/outreach-persona-api/) — <SchemaDefinition schemaRef="#/components/schemas/persona" /> ## Persona Relationships <SchemaDefinition…
- [Outreach Phone Number API](https://apis.io/apis/outreach/outreach-phone-number-api/) — <SchemaDefinition schemaRef="#/components/schemas/phoneNumber" /> ## Phone Number Relationships <SchemaDefinition…
- [Outreach Product API](https://apis.io/apis/outreach/outreach-product-api/) — <SchemaDefinition schemaRef="#/components/schemas/product" /> ## Product Relationships <SchemaDefinition…
- [Outreach Profile API](https://apis.io/apis/outreach/outreach-profile-api/) — <SchemaDefinition schemaRef="#/components/schemas/profile" /> ## Profile Resource Metadata | **METADATA NAME**| **DESCRIPTION** | **QUERY PARAM** | | --- |…
- [Outreach Prospect API](https://apis.io/apis/outreach/outreach-prospect-api/) — <SchemaDefinition schemaRef="#/components/schemas/prospect" /> ## Prospect Relationships <SchemaDefinition…
- [Outreach Prospect Note API](https://apis.io/apis/outreach/outreach-prospect-note-api/) — <SchemaDefinition schemaRef="#/components/schemas/prospectNote" /> ## Prospect Note Relationships <SchemaDefinition…
- [Outreach Purchase API](https://apis.io/apis/outreach/outreach-purchase-api/) — <SchemaDefinition schemaRef="#/components/schemas/purchase" /> ## Purchase Relationships <SchemaDefinition…
- [Outreach Recipient API](https://apis.io/apis/outreach/outreach-recipient-api/) — <SchemaDefinition schemaRef="#/components/schemas/recipient" /> ## Recipient Relationships <SchemaDefinition…
- [Outreach Role API](https://apis.io/apis/outreach/outreach-role-api/) — <SchemaDefinition schemaRef="#/components/schemas/role" /> ## Role Relationships <SchemaDefinition schemaRef="#/components/schemas/roleRelationships" /> ##…
- [Outreach Sequence API](https://apis.io/apis/outreach/outreach-sequence-api/) — <SchemaDefinition schemaRef="#/components/schemas/sequence" /> ## Sequence Relationships <SchemaDefinition…
- [Outreach Sequence State API](https://apis.io/apis/outreach/outreach-sequence-state-api/) — <SchemaDefinition schemaRef="#/components/schemas/sequenceState" /> ## Sequence State Relationships <SchemaDefinition…
- [Outreach Sequence Step API](https://apis.io/apis/outreach/outreach-sequence-step-api/) — <SchemaDefinition schemaRef="#/components/schemas/sequenceStep" /> ## Sequence Step Relationships <SchemaDefinition…
- [Outreach Sequence Template API](https://apis.io/apis/outreach/outreach-sequence-template-api/) — <SchemaDefinition schemaRef="#/components/schemas/sequenceTemplate" /> ## Sequence Template Relationships <SchemaDefinition…
- [Outreach Snippet API](https://apis.io/apis/outreach/outreach-snippet-api/) — <SchemaDefinition schemaRef="#/components/schemas/snippet" /> ## Snippet Relationships <SchemaDefinition…
- [Outreach Stage API](https://apis.io/apis/outreach/outreach-stage-api/) — <SchemaDefinition schemaRef="#/components/schemas/stage" /> ## Stage Relationships <SchemaDefinition schemaRef="#/components/schemas/stageRelationships" />…
- [Outreach Task API](https://apis.io/apis/outreach/outreach-task-api/) — <SchemaDefinition schemaRef="#/components/schemas/task" /> ## Task Relationships <SchemaDefinition schemaRef="#/components/schemas/taskRelationships" /> ##…
- [Outreach Task Disposition API](https://apis.io/apis/outreach/outreach-task-disposition-api/) — <SchemaDefinition schemaRef="#/components/schemas/taskDisposition" /> ## Task Disposition Relationships <SchemaDefinition…
- [Outreach Task Priority API](https://apis.io/apis/outreach/outreach-task-priority-api/) — <SchemaDefinition schemaRef="#/components/schemas/taskPriority" /> ## Task Priority Relationships <SchemaDefinition…
- [Outreach Task Purpose API](https://apis.io/apis/outreach/outreach-task-purpose-api/) — <SchemaDefinition schemaRef="#/components/schemas/taskPurpose" /> ## Task Purpose Relationships <SchemaDefinition…
- [Outreach Team API](https://apis.io/apis/outreach/outreach-team-api/) — <SchemaDefinition schemaRef="#/components/schemas/team" /> ## Team Relationships <SchemaDefinition schemaRef="#/components/schemas/teamRelationships" /> ##…
- [Outreach Template API](https://apis.io/apis/outreach/outreach-template-api/) — <SchemaDefinition schemaRef="#/components/schemas/template" /> ## Template Relationships <SchemaDefinition…
- [Outreach User API](https://apis.io/apis/outreach/outreach-user-api/) — <SchemaDefinition schemaRef="#/components/schemas/user" /> ## User Relationships <SchemaDefinition schemaRef="#/components/schemas/userRelationships" /> ##…
- [Outreach Webhook API](https://apis.io/apis/outreach/outreach-webhook-api/) — <SchemaDefinition schemaRef="#/components/schemas/webhook" /> ## Webhook Relationships <SchemaDefinition…
- [Outreach Rule Set API](https://apis.io/apis/outreach/outreach-rule-set-api/) — ## Ruleset Relationships ## Ruleset Resource Metadata | **METADATA NAME**| **DESCRIPTION** | **QUERY PARAM** | | --- | --- | --- | | canWrite | A boolean…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [outreach](https://apis.io/servers/outreach/outreach/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Outreach Agentic Access](https://apis.io/agentic-access/outreach/outreach-agentic-access/)

#### JSON Schema (1)

The data models the API reads and writes.

- [Outreach Hyper](https://apis.io/schemas/outreach/outreach-hyper/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Outreach Context](https://apis.io/jsonld/outreach/outreach-context/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Outreach Openapi Overlay](https://apis.io/overlays/outreach/outreach-openapi-overlay/)

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [Outreach API Rules](https://apis.io/rules/outreach/outreach-rules/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Outreach Authentication](https://apis.io/security/outreach/outreach-authentication/)
- [Outreach Domain Security](https://apis.io/security/outreach/outreach-domain-security/)
- [Outreach Trust Center](https://apis.io/security/outreach/outreach-trust-center/)
- [Outreach Vulnerability Disclosure](https://apis.io/security/outreach/outreach-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Outreach Scopes](https://apis.io/scopes/outreach/outreach-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Outreach Plans Pricing](https://apis.io/plans/outreach/outreach-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Outreach Rate Limits](https://apis.io/rate-limits/outreach/outreach-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Outreach Finops](https://apis.io/finops/outreach/outreach-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.outreach.ai/)
- [Documentation](https://developers.outreach.io/api/)
- [Getting started](https://developers.outreach.io/api/getting-started)
- [API reference](https://developers.outreach.io/api/reference)
- [Pricing](https://www.outreach.ai/pricing)
- [Sign up](https://www.outreach.ai/request-demo)
- [Support](https://support.outreach.io/support/home)
- [Blog](https://www.outreach.ai/resources/blog)
- [Security](https://www.outreach.ai/responsible-disclosure)
- [Compliance](https://www.outreach.ai/platform/trust)
- [Terms of service](https://www.outreach.ai/terms)
- [Privacy policy](https://www.outreach.ai/privacy-statement)
- [GitHub](https://github.com/getoutreach)
- [Status](https://status.outreach.io)

## API Evangelist rating

**Kin Score 79.3** — exemplar · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 76.7 |
| Contract quality | 64.0 |
| Contract governance | 35.6 |
| Operational transparency | 84.2 |
| Developer ergonomics | 66.1 |
| Access clarity | 92.1 |

**Agent readiness 53.1** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | verified |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | unknown |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 45.1** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/outreach/](https://apis.io/providers/outreach/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Outreach: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/outreach/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
