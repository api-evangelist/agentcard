---
name: Connect and consent a user
description: Connect an end user to your Agentcard platform and record their authorization, using the v2 REST API.
api: openapi/agentcard-openapi-original.json
operations: [createAccessToken, connectStart, connectVerify, connectConsent]
generated: '2026-07-17'
method: generated
---

# Connect and consent a user (Agentcard v2)

Use this to onboard one of your users to Agentcard from your own backend. Base URL is
`https://api.agentcard.sh`; sandbox vs live is decided by the credential, never the host.

## Auth

1. Mint a platform token: `createAccessToken` — `POST /api/v2/oauth/token` with
   `client_id` + `client_secret` (OAuth2 client credentials, RFC 6749 §4.4). The token lives
   one hour; re-mint on expiry (there is no refresh token on this grant).
2. Send it on every call: `Authorization: Bearer <platform_access_token>`.
3. Optional health check: `introspectCredential` — `GET /api/v2` confirms the org and mode
   the token acts as.

## Steps

1. `connectStart` — `POST /api/v2/connect/start` with **exactly one** of `email` or `phone`.
   Sends the user a one-time code (valid 10 minutes). Returns 201.
2. `connectVerify` — `POST /api/v2/connect/verify` with the code the user read back.
   Completing the code **is** the authorization — there is no separate approval screen.
   Returns the token pair to store (store both encrypted, keyed to the user).
3. `connectConsent` — `POST /api/v2/connect/consent` records that the user authorized your
   platform to act on their behalf. **Idempotent per user** — safe to retry; a repeat call
   updates the same record instead of duplicating it.

## Rules

- Branch on `error.code` in the `{ "error": { code, message, docs } }` envelope
  (see errors/agentcard-problem-types.yml). A 401 means the platform token expired — re-mint.
- A `502`/`503` from connect is an upstream provider hiccup — retry with backoff.
- Never log tokens or codes.
