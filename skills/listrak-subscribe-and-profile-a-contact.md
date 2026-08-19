---
name: Subscribe and profile a Listrak email contact
description: Add or update a contact on a Listrak email list and write their profile (segmentation) field values, without tripping Listrak's mutually-exclusive request rules.
api: openapi/listrak-contact-api-openapi.yml
base_url: https://api.listrak.com/email
operations:
  - List_GetListCollection
  - SegmentationField_GetSegmentationFieldCollection
  - Contact_PostContactResource
  - ContactSegmentationField_PostContactSegmentationFieldValuesResource
  - Contact_GetContactResourceByIdentifier
scopes: [List, Segmentation]
generated: '2026-08-13'
method: generated
source: openapi/_original/listrak-email-openapi.json
---

# Subscribe and profile a Listrak email contact

Use this to get a person onto a Listrak email list with their profile data attached. Listrak's
contact model is **per list** — a contact is not a global object, it exists on `listId`, and the same
email address on two lists is two contacts.

## Before you start

Get a token. Every call needs one and they are not long-lived.

```
POST https://auth.listrak.com/OAuth2/Token
Content-Type: application/x-www-form-urlencoded

grant_type=client_credentials&client_id=...&client_secret=...
```

Send it on every request as `Authorization: Bearer <token>`. The Integration must grant the **List**
scope (and **Segmentation** for profile fields), must not be paused, and must be called from an
allowed IP — otherwise you get `ERROR_UNAUTHORIZED` or `ERROR_INVALID_CREDENTIALS`, not a 403 with an
explanation.

## Steps

1. **Find the list.** `List_GetListCollection` — `GET /email/v1/List`. Returns `listId` +
   `listName`. Cache this; it does not change.

2. **Learn the profile fields.** `SegmentationField_GetSegmentationFieldCollection` —
   `GET /email/v1/List/{listId}/SegmentationFieldGroup/{segmentationFieldGroupId}/SegmentationField`.
   You need `segmentationFieldId`, `dataType` and `maxLength` before you write anything. Writing a
   value longer than `maxLength` or to a disabled field fails
   (`ERROR_SEGMENTATION_MAX_LENGTH`, `ERROR_SEGMENTATION_FIELD_DISABLED`).

3. **Create or update the contact.** `Contact_PostContactResource` —
   `POST /email/v1/List/{listId}/Contact`. This one operation both creates and updates; there is no
   separate PUT. Body carries `emailAddress`, `subscriptionState`, optionally `externalContactID`
   and `segmentationFieldValues`. Returns `201` with `{status, resourceId}` — the new identifier
   comes back as `resourceId`, **not** in a `Location` header.

4. **Or write profile values separately.** `ContactSegmentationField_PostContactSegmentationFieldValuesResource` —
   `POST /email/v1/List/{listId}/Contact/SegmentationField`. Use this when you are updating profile
   data for a contact that already exists and you do not want to touch subscription state.

5. **Verify.** `Contact_GetContactResourceByIdentifier` —
   `GET /email/v1/List/{listId}/Contact/{contactIdentifier}`. The identifier is the email address or
   the contact key. Pass `segmentationFieldIds` (comma-separated) to hydrate profile fields —
   **maximum 30 per request** or you get `ERROR_TOO_MANY_SEGMENTATION_FIELDS`.

## Rules that will bite you

Listrak enforces **mutual exclusion** between subscription changes, profile data, and events in a
single request. These are real error codes, not edge cases:

| Do not | Error |
|---|---|
| Change `emailAddress` while sending events | `ERROR_CHANGE_ADDRESS_WITH_EVENTS` |
| Change `emailAddress` while sending profile data | `ERROR_CHANGE_ADDRESS_WITH_SEGMENTATION_DATA` |
| Unsubscribe while sending events | `ERROR_UNSUBSCRIBE_WITH_EVENTS` |
| Unsubscribe while sending profile data | `ERROR_UNSUBSCRIBE_WITH_SEGMENTATION_DATA` |
| Update an unsubscribed contact with events | `ERROR_UPDATE_UNSUBSCRIBE_WITH_EVENTS` |

Split them into separate calls, in that order: subscription change first, then profile data, then
events.

Subscribing an address that is banned, suppressed, or already pending double opt-in fails with
`ERROR_BANNED_EMAIL_ADDRESS`, `ERROR_SUPPRESSED_EMAIL` or `ERROR_PENDING_EMAIL_ADDRESS`. Treat all
three as terminal — retrying will not change the outcome.

## Retry and pacing

**There is no idempotency key.** A retried `Contact_PostContactResource` is a second write. Because
the operation is an upsert keyed on `emailAddress`, a duplicate is usually harmless — but do not
generalize that to any other Listrak POST.

The Email API publishes no rate limit and no rate-limit headers. Back off exponentially on `429` and
`500`; there is no `Retry-After` to read. Do **not** loop this operation to load a large file —
use the list-import operations instead.

## Errors

Every failure is `application/json` shaped `{"status":…, "error":"ERROR_…", "message":"…"}`. Branch
on `error`, never on `message`. Full registry: `errors/listrak-error-codes.yml`.
