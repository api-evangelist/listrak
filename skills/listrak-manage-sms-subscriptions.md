---
name: Manage Listrak SMS subscriptions
description: Subscribe, unsubscribe and message SMS contacts through the Listrak SMS REST API, respecting double opt-in, age gates and the sender-code hierarchy.
api: openapi/listrak-contactlistsubscription-api-openapi.yml
base_url: https://api.listrak.com/sms
operations:
  - SenderCode_GetShortCodeCollection
  - PhoneList_GetListCollection
  - Contact_GetContactCollection
  - ContactListSubscription_PostContactListSubscription
  - ContactListSubscription_DeleteUnsubscribeContactListSubscription
  - TransactionalMessage_PostTransactionalMessageSend
generated: '2026-08-13'
method: generated
source: openapi/_original/listrak-sms-openapi.json
---

# Manage Listrak SMS subscriptions

The SMS API hangs everything off a **sender code** (a short or long code), not off a list. The
hierarchy is `ShortCode/{senderCodeId}` → `PhoneList/{phoneListId}` → contact by `phoneNumber`. Get
that wrong and you get `ERROR_INVALID_LIST_ID`, which really means "that list is not on that sender
code".

## Before you start

Token from `https://auth.listrak.com/OAuth2/Token`. The SMS API declares OAuth2 with an **empty
scope map** — access is governed by the Integration's configured access level in the Listrak
application, not by a scope string, so there is nothing to request in the token.

## Steps

1. **List sender codes.** `SenderCode_GetShortCodeCollection` — `GET /sms/v1/ShortCode`. Returns
   `shortCodeId`, `code`, `country`, `merchantName`, and — usefully — `emailListId`, the email list
   this sender code is paired with. That field is the only published join between Listrak's SMS and
   email identity models.

2. **List phone lists on the code.** `PhoneList_GetListCollection` —
   `GET /sms/v1/ShortCode/{senderCodeId}/PhoneList`. Read `requireDoubleOptIn`, `requireAgeGate`,
   `messageLimit` and `messageLimitTimeFrame` before you subscribe anyone — those settings change
   what step 3 actually does.

3. **Subscribe.** `ContactListSubscription_PostContactListSubscription` —
   `POST /sms/v1/ShortCode/{senderCodeId}/Contact/{phoneNumber}/PhoneList/{phoneListId}`.
   If the list requires double opt-in the contact lands in a **pending** state, not subscribed —
   the confirmation is a carrier round-trip you do not control. Re-posting a pending number returns
   `ERROR_PENDING_PHONE_NUMBER`; re-posting a subscribed one returns
   `ERROR_SUBSCRIBED_PHONE_NUMBER`. Both are terminal, not retryable.

4. **Read subscribers.** `Contact_GetContactCollection` —
   `GET /sms/v1/ShortCode/{senderCodeId}/PhoneList/{phoneListId}/Contact`. Page with `cursor` +
   `count`, follow `nextPageCursor`.

5. **Unsubscribe.** `ContactListSubscription_DeleteUnsubscribeContactListSubscription` —
   `DELETE /sms/v1/ShortCode/{senderCodeId}/ContactUnsubscribe/{phoneNumber}/PhoneList/{phoneListId}`.
   Note the route segment is `ContactUnsubscribe`, not `Contact`.

6. **Send a transactional SMS.** `TransactionalMessage_PostTransactionalMessageSend` —
   `POST /sms/v1/ShortCode/{SenderCodeId}/PhoneList/{phoneListId}/TransactionalMessage/{transactionalMessageId}/Message`.
   The message must already exist in the application. Note the capitalised `{SenderCodeId}` on this
   route — Listrak is inconsistent about the casing between routes, so build the path from the spec
   rather than by string-templating one convention everywhere.

## Compliance is not optional here

SMS carries obligations the email side does not. Do not work around them:

- Never subscribe a number the user did not consent to. `requireDoubleOptIn` and `requireAgeGate`
  exist to make consent provable; a pending contact that never confirms must stay unsent-to.
- `ERROR_BANNED_PHONE_NUMBER` means the number is banned from that sender code. Do not retry, do not
  try a different code.
- `ERROR_PHONE_NUMBER_SUSPENDED` means carrier-side suspension. Nothing you send will arrive.
- `ERROR_LIST_INACTIVE` / `ERROR_SENDER_CODE_DISABLED` mean the messaging program itself is off.
  Escalate to a human rather than retrying.

## Retry and pacing

No idempotency key — a retried send is a second text message, with real cost and real regulatory
exposure. Retry only on `429` and `5xx`.

The SMS API publishes no API rate limit and no rate-limit headers. Separately, throughput is bounded
by carrier and short-code capacity and by the account's contracted volume, so sustained bursts will
queue or fail regardless of what the API accepts.

## Errors

`{"status":…, "error":"ERROR_…", "message":"…"}`. Branch on `error`.
Full registry: `errors/listrak-error-codes.yml`.
