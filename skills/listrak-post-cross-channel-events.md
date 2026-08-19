---
name: Post Listrak cross-channel custom events
description: Discover a Listrak custom event configuration, read its JSON schema at runtime, and post conforming events to drive Journey Hub automations.
api: openapi/listrak-events-api-openapi.yml
base_url: https://api.listrak.com/crosschannel/v1
operations:
  - getEventConfigurations
  - getSchemaByEventUid
  - postEvents
generated: '2026-08-13'
method: generated
source: openapi/_original/listrak-crosschannel-openapi.json
---

# Post Listrak cross-channel custom events

The Cross Channel API is how arbitrary business events — a return started, a service appointment
booked, a loyalty tier changed — get into Listrak and trigger Journey Hub automations across email,
SMS and push.

It has a property almost nothing else in Listrak has: **the contract is retrievable at runtime**.
Each event type is declared as an Event Configuration with a UID and a JSON schema, and you can fetch
that schema before you post. Use it. Do not hardcode a payload shape.

## Before you start

Token from `https://auth.listrak.com/OAuth2/Token`, sent as `Authorization: Bearer <token>`. The
Integration must be of type **Cross Channel** — this is a distinct integration type from Email or
SMS, and an Email integration's credentials will not work here.

The Cross Channel API is fronted by an AWS API Gateway custom authorizer, so its spec declares the
`Authorization` header rather than an OAuth2 flow. It is the same token.

## Steps

1. **List event configurations.** `getEventConfigurations` —
   `GET /crosschannel/v1/eventConfigurations`. Returns every declared custom event type with its
   `eventUID`. Event configurations are created in the Listrak application; the API cannot create
   one.

2. **Fetch the schema for the one you want.** `getSchemaByEventUid` —
   `GET /crosschannel/v1/eventConfigurations/{eventUID}`. Returns the configuration detail including
   the JSON schema the event payload must satisfy. Validate against this locally before posting —
   it is far cheaper than reading a `400` back.

3. **Post events.** `postEvents` —
   `POST /crosschannel/v1/eventConfigurations/{eventUID}/events`. Takes a list of events with their
   recipient identifiers. The response carries per-recipient detail, so a partial failure is
   reported per recipient rather than failing the whole batch — read the response body even on a
   success status.

## Design notes

- **Refetch the schema periodically.** A configuration can change in the application without any
  version bump reaching you. Cache the schema with a TTL rather than pinning it at build time.
- **Recipient identity is yours to get right.** The event names the contact; Listrak matches it into
  its own identity graph. Send the identifier the account is configured to match on and be
  consistent, or events will land against the wrong profile or none.
- **This is inbound, not a webhook.** Events flow *into* Listrak. Listrak's only outbound webhook is
  on the Two-Way SMS API (`asyncapi/listrak-webhooks.yml`); email and SMS engagement events have to
  be polled from the reporting operations.

## Retry and pacing

No idempotency key. A retried batch posts the events again, and duplicate events can re-trigger a
journey — meaning a duplicate message to a real person. Retry only on `429` and `5xx`, and prefer
narrowing the retry to the recipients the response reported as failed rather than re-posting the
whole batch.

The Cross Channel API publishes no rate limit and no rate-limit headers. Back off exponentially;
there is no `Retry-After`.

## Errors

`{"status":…, "error":"ERROR_…", "message":"…"}` on `application/json`, plus per-recipient error
detail in the response body on partial failures. Full registry: `errors/listrak-error-codes.yml`.
