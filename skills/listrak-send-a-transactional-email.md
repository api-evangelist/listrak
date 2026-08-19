---
name: Send a Listrak transactional email
description: Send, track and resend a transactional email message through the Listrak Email REST API, including the checks that must happen before the send.
api: openapi/listrak-transactionalmessage-api-openapi.yml
base_url: https://api.listrak.com/email
operations:
  - TransactionalMessage_GetTransactionalMessageCollection
  - TransactionalMessage_GetTransactionalMessageResource
  - TransactionalMessage_PostTransactionalMessageSend
  - TransactionalMessageActivity_GetTransactionalMessageActivityCollection
  - TransactionalMessageResend_PostTransactionalMessageResend
scopes: [Message]
generated: '2026-08-13'
method: generated
source: openapi/_original/listrak-email-openapi.json
---

# Send a Listrak transactional email

Transactional messages in Listrak are **pre-built in the application**. The API does not author the
message — it triggers an existing `transactionalMessageId` for a recipient and merges profile values
into it. If the message does not exist in the UI, no API call will create it.

## Before you start

Token from `https://auth.listrak.com/OAuth2/Token` (client_credentials), sent as
`Authorization: Bearer <token>`. The Integration needs the **Message** scope.

## Steps

1. **Find the message.** `TransactionalMessage_GetTransactionalMessageCollection` —
   `GET /email/v1/List/{listId}/TransactionalMessage`. Returns the transactional messages configured
   on the list with their `transactionalMessageId`. Do this once and cache; do not look it up on
   every send.

2. **Inspect one if you need to.** `TransactionalMessage_GetTransactionalMessageResource` —
   `GET /email/v1/List/{listId}/TransactionalMessage/{transactionalMessageId}`.

3. **Send.** `TransactionalMessage_PostTransactionalMessageSend` —
   `POST /email/v1/List/{listId}/TransactionalMessage/{transactionalMessageId}/Message`. The body
   carries the recipient and the `segmentationFieldValues` to merge. Supply each
   `segmentationFieldId` **at most once** — two values for the same field is
   `ERROR_SEGMENTATION_FIELD_DEFINED_TWICE`.

4. **Check delivery and engagement.** `TransactionalMessageActivity_GetTransactionalMessageActivityCollection` —
   `GET /email/v1/List/{listId}/TransactionalMessage/{transactionalMessageId}/Activity`. This is
   **polling**. Listrak publishes no webhook for email engagement events, so activity has to be
   pulled on an interval. Page it with `cursor` + `count` (default 1000, max 5000) and follow
   `nextPageCursor` until it is empty.

5. **Resend if needed.** `TransactionalMessageResend_PostTransactionalMessageResend` —
   `POST /email/v1/List/{listId}/TransactionalMessage/{transactionalMessageId}/Resend/{resendKey}`.
   The `resendKey` comes from the original send; this is Listrak's controlled way to re-deliver, and
   it is safer than re-issuing step 3.

## Rules that will bite you

Message content is validated at send time, not at configuration time:

- `ERROR_TRANSACTIONAL_MESSAGE_EXTERNAL_CONTENT` — the message body contains external content tags.
- `ERROR_TRANSACTIONAL_MESSAGE_SYSTEM_LINK` — the message body contains system link tags.

Both are content problems in the UI-authored message; retrying the send will keep failing until
someone edits the message.

Flag combinations on the broader message operations are also mutually exclusive:
`ERROR_TEST_FLAG_AND_REVIEW_FLAG_SET`, `ERROR_TEST_FLAG_AND_SEND_DATE_SET`,
`ERROR_REVIEW_FLAG_AND_SEND_DATE_SET`.

## Retry — read this before you build a retry loop

**Listrak publishes no idempotency key.** A retried
`TransactionalMessage_PostTransactionalMessageSend` sends a second email. There is no request
deduplication and no way to ask Listrak whether a send already happened for a given request.

Therefore:

- Treat any `2xx` as delivered and do not retry it.
- On a **network timeout with no response**, do **not** blindly retry. Poll
  `TransactionalMessageActivity_GetTransactionalMessageActivityCollection` for the recipient first.
- Retry only on `429` and `5xx`, with exponential backoff. There is no `Retry-After` header to read.
- Use `TransactionalMessageResend_PostTransactionalMessageResend` for a deliberate re-delivery
  rather than repeating the send.

## Errors

`{"status":…, "error":"ERROR_…", "message":"…"}` on `application/json`. Branch on `error`.
Full registry: `errors/listrak-error-codes.yml`.
