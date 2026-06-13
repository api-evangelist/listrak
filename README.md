# Listrak (listrak)

Listrak is a retail digital marketing platform with a REST API for managing email and SMS campaigns, subscriber data, behavioral triggers, and cross-channel marketing automation. Trusted by over 1,000 leading retail brands, Listrak unifies customer engagement across email, SMS, MMS, RCS, push notifications, web personalization, and in-store channels from a single platform.

APIs.json: https://raw.githubusercontent.com/api-evangelist/listrak/refs/heads/main/apis.yml

Naftiko: https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=listrak-api-evangelist&utm_content=repo

## Tags

Email Marketing, SMS Marketing, Marketing Automation, Cross-Channel, Retail, Push Notifications, Data Import, Privacy

## APIs

Listrak exposes seven REST APIs covering the full scope of its retail marketing platform:

| API | Description | Docs |
|-----|-------------|------|
| Email REST API | Manage contacts, execute email campaigns, retrieve metrics | https://api.listrak.com/email |
| SMS REST API | Subscriber management, list management, transactional SMS | https://api.listrak.com/sms |
| Cross Channel REST API | Custom events for Journey Hub cross-channel automations | https://api.listrak.com/crosschannel/v1/docs |
| Data Import REST API | Ingest customers, orders, products, and reviews | https://api.listrak.com/data |
| Two-Way SMS Conversation API | Real-time two-way SMS for customer support integrations | https://api.listrak.com/twowaysms/docs |
| Mobile App Push API | Device registration, push notifications, app engagement | https://api.listrak.com/mobileclient/docs |
| Privacy REST API | CCPA / GDPR contact removal and data forget requests | https://api.listrak.com/privacy |

All APIs authenticate via OAuth 2.0 client credentials. Obtain a Bearer token from `https://auth.listrak.com/OAuth2/Token`.

## Plans, Rate Limits, and FinOps

- **Plans:** [plans/listrak-plans-pricing.yml](plans/listrak-plans-pricing.yml) — Listrak uses custom enterprise pricing. No self-service tiers are published. Annual contracts are estimated between $37,000 and $146,000 depending on contact volume and channels activated.
- **Rate Limits:** [rate-limits/listrak-rate-limits.yml](rate-limits/listrak-rate-limits.yml) — Specific rate limit thresholds are not publicly documented. All APIs use OAuth 2.0 Bearer tokens. Payload size limits apply; violations return a 404 response.
- **FinOps:** [finops/listrak-finops.yml](finops/listrak-finops.yml) — Primary cost drivers are contact database size, monthly message volume across channels, and add-on features such as Listrak Intelligence AI recommendations and Journey Hub orchestration.

## Timestamps

- **Created:** 2026-06-13
- **Modified:** 2026-06-13

## Common

| Type | URL |
|------|-----|
| Website | https://www.listrak.com/ |
| Documentation | https://www.listrak.com/learn/developers |
| GitHub Org | https://github.com/InfernoRed/listrak-mobile-ios |
| LinkedIn | https://www.linkedin.com/company/listrak/ |
| Blog | https://www.listrak.com/learn/blog |
| Pricing | https://www.listrak.com/ |
| Status Page | https://status.listrak.com |
| X | https://twitter.com/Listrak |

## Maintainers

**Kin Lane** — kin@apievangelist.com
