---
name: Honor a GDPR/CCPA forget request in Listrak
description: Submit and track a consumer data-deletion (forget) request through the Listrak Privacy REST API, the one Listrak API that exists purely to serve a regulatory obligation.
api: openapi/listrak-forget-api-openapi.yml
base_url: https://api.listrak.com/privacy
operations:
  - Forget_PostForgetRequest
  - Forget_GetForgetRequest
generated: '2026-08-13'
method: generated
source: openapi/_original/listrak-privacy-openapi.json
---

# Honor a GDPR/CCPA forget request in Listrak

Two operations. Submit a forget request for a consumer, then poll it until it completes. This is the
API a retailer wires into its data-subject-request workflow so deletion in Listrak is not a manual
support ticket.

## Before you start

Token from `https://auth.listrak.com/OAuth2/Token` (client_credentials). The Integration must be of
type **Privacy**. This API declares OAuth2 with an empty scope map — access is controlled by the
Integration's configuration, not by a scope string.

## Steps

1. **Submit the request.** `Forget_PostForgetRequest` — `POST /privacy/v1/Forget`. The body carries
   the identifiers of the consumer to forget. Returns `201` with `{status, resourceId}` — keep
   `resourceId`, it is the request ID and it is the only handle you get.

2. **Poll for completion.** `Forget_GetForgetRequest` — `GET /privacy/v1/Forget/{requestId}`.
   Deletion is asynchronous. Poll on an interval and record the terminal state against your own DSR
   record — that record, not Listrak's, is what you will show a regulator.

## Rate limits — the only ones Listrak publishes

This is the **one** Listrak API with a published numeric limit, stated in its own specification:

| Limit | Period |
|---|---|
| 20 requests | 10 seconds |
| 60 requests | 1 minute |

Both windows apply together: 20 per 10 seconds is the burst ceiling, 60 per minute is the sustained
ceiling, so you cannot spend the 10-second allowance six times in a minute. Exhaustion returns `429`
with **no** `Retry-After` header, so pace deliberately rather than reacting.

If you are processing a backlog of deletion requests, that ceiling — 60/minute — is your throughput
budget. Queue the work; do not fan it out.

## Handle it like the compliance operation it is

- **Do not retry a `2xx`.** There is no idempotency key. A duplicate submission creates a second
  request; it will not corrupt anything, but it burns your rate budget and muddies your audit trail.
- **Log everything.** Store the `resourceId`, the submission timestamp, every poll result and the
  terminal state. Regulatory deadlines are counted from when the consumer asked, not from when you
  called the API.
- **Deletion is not reversible.** Confirm consumer identity in your own system before calling
  `Forget_PostForgetRequest`; Listrak will not verify it for you.
- **Listrak is one processor of many.** Forgetting a consumer here does not forget them in your
  commerce platform, your CDP, or your warehouse. This step belongs inside a wider DSR workflow.

## Errors

`{"status":…, "error":"ERROR_…", "message":"…"}` on `application/json`. `401` /
`ERROR_UNAUTHORIZED` on a bad or expired token, `400` / `ERROR_INVALID_PARAMETER` on a malformed
identifier, `404` on an unknown `requestId`. Full registry: `errors/listrak-error-codes.yml`.
