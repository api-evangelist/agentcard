---
name: Fund a user's wallet
description: Take a connected Agentcard user through phone verification and wallet funding, using the v2 REST API.
api: openapi/agentcard-openapi-original.json
operations: [walletGet, walletPhoneStart, walletPhoneVerify, walletFund, walletFundStatus]
generated: '2026-07-17'
method: generated
---

# Fund a user's wallet (Agentcard v2)

Cards are funded from the user's wallet. Funding requires a phone verification fresh within
60 days. Authenticate with a platform Bearer token (see the connect skill).

## Steps

1. `walletGet` — `GET /api/v2/wallet` returns the user's wallet and balance (provisions it on
   first read). Render it in your own wallet UI.
2. Phone verification (once per 60 days):
   - `walletPhoneStart` — `POST /api/v2/wallet/phone/start` sends the user a one-time code
     (provide `phone_number` only if none is on file; US numbers only). May return `429` if
     codes are requested too often.
   - `walletPhoneVerify` — `POST /api/v2/wallet/phone/verify` with the code the user read
     back. On success the verification stays fresh for 60 days.
3. `walletFund` — `POST /api/v2/wallet/fund` returns an Apple Pay / Google Pay payment link
   for the amount you specify. Show it in your UI; the link is **single-use and expires after
   30 minutes**. Funds land in the wallet when the user completes payment.
4. `walletFundStatus` — `GET /api/v2/wallet/fund/{session_id}` polls the funding session until
   `completed` (the payment status is refreshed from the provider on every read).

## Rules

- Amounts on the REST/MCP surface are in **cents** (`2500` = $25.00) — always convert; carrying
  `25` verbatim creates a $0.25 charge.
- Handle `409` (wallet state) and `422` (validation) via `error.code`; `502`/`503` are upstream
  payment-provider hiccups — retry with backoff.
