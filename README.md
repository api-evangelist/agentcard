# Agentcard

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

Agentcard is a Y Combinator (Summer 2026) startup building card-issuing payments infrastructure for AI agents. It issues virtual Visa cards that are funded with a fixed USD amount and close after their first charge, giving agents scoped, single-use spending power with hard budget limits and no overdraft risk. Access is available three ways over one host: a REST v2 API, a hosted Model Context Protocol (MCP) server, and first-party CLIs. There are two products: Personal (an individual gives their own agent a card, funded via Apple Pay / Google Pay) and Companies ("Connect with Agentcard" — a platform issues cards to many users through OAuth 2.1 + PKCE). The platform covers user connect, identity verification (KYC), wallet funding, withdrawals, virtual card creation, transactions, and merchant shopping (buy) with HMAC-signed webhooks and a sandbox mode split from live by credential.

**Areas:** Company · Payments · Virtual Cards · Card Issuing · AI Agents · Agentic Commerce · MCP · Fintech · Wallets · Visa · A2A

## Agentcard on APIs.io

Everything profiled for Agentcard is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/agentcard/](https://apis.io/providers/agentcard/)** — or go straight to one of the APIs or properties below.

### APIs (5)

- [Agentcard Authentication API](https://apis.io/apis/agentcard/agentcard-authentication-api/) — Exchange your client credentials for a platform access token, and introspect what a token acts as.
- [Agentcard Connect API](https://apis.io/apis/agentcard/agentcard-connect-api/) — Connect a user to your platform: send a one-time code, verify it, record consent, and keep the connection alive.
- [Agentcard Identity verification API](https://apis.io/apis/agentcard/agentcard-identity-verification-api/) — Verify a connected user's identity: upload their ID, submit any extra fields we ask for, then show a short face scan.
- [Agentcard Wallet funding API](https://apis.io/apis/agentcard/agentcard-wallet-funding-api/) — Fund a connected user's wallet from your own UI — request a payment link, relay the phone verification code, and poll until the funds land.
- [Agentcard Withdrawals API](https://apis.io/apis/agentcard/agentcard-withdrawals-api/) — Move money out of a connected user's wallet — to a saved bank account or a crypto address on Base. Transfers are processed manually by the Agentcard team,…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### Arazzo workflows (2)

Multi-step workflows that chain operations into a business task.

- [Agentcard — connect a user and verify identity](https://apis.io/arazzos/agentcard/agentcard-connect-and-verify.arazzo/)
- [Agentcard — verify phone and fund wallet](https://apis.io/arazzos/agentcard/agentcard-fund-wallet.arazzo/)

#### AsyncAPI (2)

Event-driven and webhook contracts.

- [Agentcard Webhooks](https://apis.io/asyncapis/agentcard/agentcard-webhooks/)
- [Agentcard Webhooks](https://apis.io/asyncapis/agentcard/agentcard-webhooks-asyncapi/)

#### Event channels (1)

Individual events and webhooks the provider emits.

- [/webhooks/agentcard](https://apis.io/channels/agentcard/webhooks-agentcard/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [Agentcard](https://apis.io/servers/agentcard/agentcard/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Agentcard Agentic Access](https://apis.io/agentic-access/agentcard/agentcard-agentic-access/)

#### Collections (5)

Postman and Open Collection request collections.

- [Agentcard Authentication API](https://apis.io/collections/agentcard/open-agentcard-authentication-api/)
- [Agentcard Authentication Connect API](https://apis.io/collections/agentcard/open-agentcard-connect-api/)
- [Agentcard Authentication Identity verification API](https://apis.io/collections/agentcard/open-agentcard-identity-verification-api/)
- [Agentcard Authentication Wallet funding API](https://apis.io/collections/agentcard/open-agentcard-wallet-funding-api/)
- [Agentcard Authentication Withdrawals API](https://apis.io/collections/agentcard/open-agentcard-withdrawals-api/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Agentcard V2 Overlay](https://apis.io/overlays/agentcard/agentcard-v2-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Agentcard Authentication](https://apis.io/security/agentcard/agentcard-authentication/)
- [Agentcard Domain Security](https://apis.io/security/agentcard/agentcard-domain-security/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.agentcard.sh)
- [Documentation](https://docs.agentcard.sh)
- [Getting started](https://docs.agentcard.sh/companies/getting-started/quickstart)
- [API reference](https://docs.agentcard.sh/companies/api/reference)
- [Pricing](https://docs.agentcard.sh/personal/plans)
- [Sign up](https://app.agentcard.sh)
- [Support](https://docs.agentcard.sh/personal/support)
- [Blog](https://www.agentcard.sh/blog/)
- [Terms of service](https://www.agentcard.sh/terms)
- [Privacy policy](https://www.agentcard.sh/privacy)
- [GitHub](https://github.com/agentcard)
- [Status](https://agentcard.checkly-status-page.com)

## API Evangelist rating

**Kin Score 52.9** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 58.8 |
| Contract governance | 4.5 |
| Operational transparency | 26.3 |
| Developer ergonomics | 90.5 |
| Access clarity | 44.7 |

**Agent readiness 72.2** — agent-native

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | verified |
| Auth Clarity | served (partial credit) |
| Idempotency | verified |
| Error Semantics | verified |
| OpenAPI Examples | verified |
| Rate Limit Signal | — |
| Event Surface Described | yes |
| Agent Skills | yes |
| Well Known Catalog | yes |
| Consent Identity | — |
| Agent Card | flavored (partial credit) |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 22.3** — Payments

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/agentcard/](https://apis.io/providers/agentcard/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Agentcard: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/agentcard/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
