# Listrak (listrak)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
