---
name: Verify a user's identity (KYC)
description: Run a connected Agentcard user through identity verification before card issuance, using the v2 REST API.
api: openapi/agentcard-openapi-original.json
operations: [kycGetStatus, kycUploadFront, kycUploadBack, kycSubmitInformation, kycSimulate]
generated: '2026-07-17'
method: generated
---

# Verify a user's identity (Agentcard v2 KYC)

Identity verification is required once per user before their first card. Authenticate with a
platform Bearer token (see the connect skill).

## Steps

1. `kycGetStatus` — `GET /api/v2/kyc` polls the current verification status (the alternative
   to the `identity.verification.updated` webhook).
2. `kycUploadFront` — `POST /api/v2/kyc/documents/front` with the front of the ID as a
   base64 image. Acknowledges receipt; the next step (`back`) tells you what comes next.
3. `kycUploadBack` — `POST /api/v2/kyc/documents/back`. **This is the branch point** — the
   response tells you what to do next (a face scan `iframe_url`, or a `needs_information`
   requirement).
4. `kycSubmitInformation` — `POST /api/v2/kyc/information` only when a `needs_information`
   response asks for extra fields. Send only the fields named in `required_fields`; on success
   the response returns the `iframe_url` for the face scan.
5. Poll `kycGetStatus` (or handle the webhook) until terminal.

## Test mode

- `kycSimulate` — `POST /api/v2/kyc/simulate` (test credentials only) drives a verification to
  `approved`, `rejected`, or `requires_input` instantly and fires the same
  `identity.verification.updated` webhook a real review produces. Returns `403 sandbox_only`
  on live credentials.

## Rules

- Handle `409` (state does not permit the step) by re-reading `kycGetStatus` and resuming at
  the correct step. `422` on an upload returns `warnings[]` that are safe to show the user.
- `502` is an upstream KYC-provider error — retry with backoff.
