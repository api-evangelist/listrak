---
name: Sync retail data into Listrak
description: Push customers, orders, products, reviews and rating summaries into Listrak through the Data Import REST API so segmentation, recommendations and abandonment journeys have something to work with.
api: openapi/listrak-customer-api-openapi.yml
base_url: https://api.listrak.com/data
operations:
  - Customer_PostCustomerCollection
  - Order_PostOrderCollection
  - Product_PostProductCollection
  - Review_PostReviewCollection
  - RatingSummary_PostRatingSummaryCollection
scopes: [Customer, Order, Product, Review]
generated: '2026-08-13'
method: generated
source: openapi/_original/listrak-data-openapi.json
---

# Sync retail data into Listrak

The Data Import REST API is five bulk-collection POSTs. Every one takes an **array** of records and
upserts on the merchant's own key — `customerNumber`, `orderNumber`, `sku`, `providerReviewID`,
`providerProductID`. That key discipline is what makes these safe to re-run; nothing else in Listrak
gives you that.

## Before you start

Token from `https://auth.listrak.com/OAuth2/Token`. The Integration must be of type **Data** and must
grant the scope for each collection you write — Customer, Order, Product, Review.

## Order matters

Load in dependency order or you will create orphans:

1. `Product_PostProductCollection` — `POST /data/v1/Product`
2. `Customer_PostCustomerCollection` — `POST /data/v1/Customer`
3. `Order_PostOrderCollection` — `POST /data/v1/Order`
4. `Review_PostReviewCollection` — `POST /data/v1/Review`
5. `RatingSummary_PostRatingSummaryCollection` — `POST /data/v1/RatingSummary`

Orders carry their line items inline (`items[]`, each with its own `sku`, `quantity`, `price`,
`status`, `shipDate`, `trackingNumber`), so products should exist first for recommendations and
abandonment content to resolve. Reviews and rating summaries reference a product by
`providerProductID`, which the product exposes as `reviewProductID`.

## Field notes worth knowing

- **Customer** carries nested `address`, `loyalty` and `social` objects plus `meta1`–`meta5`.
- **Order** carries `billingAddress`, `shippingAddress`, `items[]`, and separate merchandise vs
  non-merchandise discount fields — Listrak models those distinctly, do not collapse them.
- **Product** has the widest surface: `price`/`msrp`/`salePrice`/`unitCost`, `inStock`/`qoh`,
  `isPurchasable`/`isViewable`/`discontinued`, three alternate-image collections, `relatedProducts`,
  and `tags`. Merchandising journeys read these flags directly, so send them honestly rather than
  defaulting them.
- **`meta1`–`meta5`** are the only extensibility. There are exactly five untyped string slots per
  entity, on Customer, Order, OrderItem and Product. There is no arbitrary metadata map. Decide what
  each slot means and write it down before you start using them.

## Batching and pacing

Listrak publishes **no** documented batch-size cap and **no** rate limit for the Data Import API.
What it does publish is a trap: a request that exceeds an undisclosed payload size limit returns
**`404 Not Found`**, not `413`. If a large batch starts 404-ing while a small one succeeds against
the same route, the route is fine and your payload is too big — halve the batch.

Start at a few hundred records per request, measure, and back off exponentially on `429` and `5xx`.
For an initial full-catalog or full-history load, use Listrak's **FTP import** instead — that is
what it exists for.

## Re-running is safe here (and only here)

There is no idempotency key anywhere in Listrak. These five operations are nonetheless safe to
re-run, because they upsert on the merchant key you supply. Do not carry that assumption into the
Email or SMS APIs — a repeated send is a second message.

Keep the key stable. If `customerNumber` or `sku` changes between runs you will create a duplicate
record rather than update the existing one, and there is no merge operation to fix it afterwards.

## Errors

`{"status":…, "error":"ERROR_…", "message":"…"}`. `ERROR_INVALID_PARAMETER` on a bad record,
`ERROR_MALFORMED_REQUEST_BODY` on bad JSON, `ERROR_UNSUPPORTED_CONTENT_TYPE` if you forget
`Content-Type: application/json`. Full registry: `errors/listrak-error-codes.yml`.
