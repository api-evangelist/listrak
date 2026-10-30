# Listrak

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

Listrak is a retail customer-engagement platform whose public API surface is eight separate REST APIs served from api.listrak.com: Email (83 operations), SMS (20), Data Import (5), Media (9), Mobile App Push (5), Two-Way SMS (4), Cross Channel custom events (3) and Privacy (2). Together they cover contacts and lists, message authoring and transactional sends, profile-field segmentation, behavioral events that drive Journey Hub automations, bulk upsert of retail customers, orders, products and reviews, media library management, mobile device registration, two-way SMS support conversations, and GDPR/CCPA forget requests. Every server-side API authenticates with OAuth 2.0 client_credentials against a single token endpoint at auth.listrak.com, returns a consistent {status, error, message} envelope drawn from a published 68-code error registry, and pages with cursor plus count.

**Areas:** Email Marketing · SMS Marketing · Marketing Automation · Cross-Channel · Retail · Push Notifications · Data Import · Privacy · E-Commerce · Customer Data · Transactional Messaging · Segmentation

## Listrak on APIs.io

Everything profiled for Listrak is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/listrak/](https://apis.io/providers/listrak/)** — or go straight to one of the APIs or properties below.

### APIs (56)

- [Listrak App Push Mobile Client Device API](https://apis.io/apis/listrak/listrak-app-push-mobile-client-device-api/) — Endpoints to manage app push devices.
- [Listrak App Push Mobile Client Engagements API](https://apis.io/apis/listrak/listrak-app-push-mobile-client-engagements-api/) — Endpoints to manage app push mobile client engagements.
- [Listrak BroadcastMessage API](https://apis.io/apis/listrak/listrak-broadcastmessage-api/) — The BroadcastMessage API from Listrak — 1 operation(s) for broadcastmessage.
- [Listrak Campaign API](https://apis.io/apis/listrak/listrak-campaign-api/) — The Campaign API from Listrak — 2 operation(s) for campaign.
- [Listrak Contact API](https://apis.io/apis/listrak/listrak-contact-api/) — The Contact API from Listrak — 8 operation(s) for contact.
- [Listrak ContactListSubscription API](https://apis.io/apis/listrak/listrak-contactlistsubscription-api/) — The ContactListSubscription API from Listrak — 3 operation(s) for contactlistsubscription.
- [Listrak ContactSegmentationField API](https://apis.io/apis/listrak/listrak-contactsegmentationfield-api/) — The ContactSegmentationField API from Listrak — 1 operation(s) for contactsegmentationfield.
- [Listrak Content API](https://apis.io/apis/listrak/listrak-content-api/) — The Content API from Listrak — 2 operation(s) for content.
- [Listrak ContentFolder API](https://apis.io/apis/listrak/listrak-contentfolder-api/) — The ContentFolder API from Listrak — 1 operation(s) for contentfolder.
- [Listrak Conversation API](https://apis.io/apis/listrak/listrak-conversation-api/) — The Conversation API from Listrak — 2 operation(s) for conversation.
- [Listrak ConversationMessage API](https://apis.io/apis/listrak/listrak-conversationmessage-api/) — The ConversationMessage API from Listrak — 2 operation(s) for conversationmessage.
- [Listrak ConversationMessageActivity API](https://apis.io/apis/listrak/listrak-conversationmessageactivity-api/) — The ConversationMessageActivity API from Listrak — 1 operation(s) for conversationmessageactivity.
- [Listrak ConversationMessageLink API](https://apis.io/apis/listrak/listrak-conversationmessagelink-api/) — The ConversationMessageLink API from Listrak — 2 operation(s) for conversationmessagelink.
- [Listrak ConversationMessageLinkClicker API](https://apis.io/apis/listrak/listrak-conversationmessagelinkclicker-api/) — The ConversationMessageLinkClicker API from Listrak — 1 operation(s) for conversationmessagelinkclicker.
- [Listrak ConversationMessageSummary API](https://apis.io/apis/listrak/listrak-conversationmessagesummary-api/) — The ConversationMessageSummary API from Listrak — 1 operation(s) for conversationmessagesummary.
- [Listrak ConversationSummary API](https://apis.io/apis/listrak/listrak-conversationsummary-api/) — The ConversationSummary API from Listrak — 1 operation(s) for conversationsummary.
- [Listrak Customer API](https://apis.io/apis/listrak/listrak-customer-api/) — The Customer API from Listrak — 1 operation(s) for customer.
- [Listrak Event API](https://apis.io/apis/listrak/listrak-event-api/) — The Event API from Listrak — 2 operation(s) for event.
- [Listrak EventGroup API](https://apis.io/apis/listrak/listrak-eventgroup-api/) — The EventGroup API from Listrak — 2 operation(s) for eventgroup.
- [Listrak Events API](https://apis.io/apis/listrak/listrak-events-api/) — REST endpoints to manage Custom Events.
- [Listrak Folder API](https://apis.io/apis/listrak/listrak-folder-api/) — The Folder API from Listrak — 2 operation(s) for folder.
- [Listrak Forget API](https://apis.io/apis/listrak/listrak-forget-api/) — The Forget API from Listrak — 2 operation(s) for forget.
- [Listrak List API](https://apis.io/apis/listrak/listrak-list-api/) — The List API from Listrak — 2 operation(s) for list.
- [Listrak ListImportContact API](https://apis.io/apis/listrak/listrak-listimportcontact-api/) — The ListImportContact API from Listrak — 1 operation(s) for listimportcontact.
- [Listrak ListImportStatus API](https://apis.io/apis/listrak/listrak-listimportstatus-api/) — The ListImportStatus API from Listrak — 1 operation(s) for listimportstatus.
- [Listrak ListImportSummary API](https://apis.io/apis/listrak/listrak-listimportsummary-api/) — The ListImportSummary API from Listrak — 1 operation(s) for listimportsummary.
- [Listrak Message API](https://apis.io/apis/listrak/listrak-message-api/) — The Message API from Listrak — 2 operation(s) for message.
- [Listrak MessageActivity API](https://apis.io/apis/listrak/listrak-messageactivity-api/) — The MessageActivity API from Listrak — 1 operation(s) for messageactivity.
- [Listrak MessageLink API](https://apis.io/apis/listrak/listrak-messagelink-api/) — The MessageLink API from Listrak — 2 operation(s) for messagelink.
- [Listrak MessageLinkClicker API](https://apis.io/apis/listrak/listrak-messagelinkclicker-api/) — The MessageLinkClicker API from Listrak — 1 operation(s) for messagelinkclicker.
- [Listrak MessageStatus API](https://apis.io/apis/listrak/listrak-messagestatus-api/) — The MessageStatus API from Listrak — 1 operation(s) for messagestatus.
- [Listrak Messagestream API](https://apis.io/apis/listrak/listrak-messagestream-api/) — The Messagestream API from Listrak — 1 operation(s) for messagestream.
- [Listrak MessageSummary API](https://apis.io/apis/listrak/listrak-messagesummary-api/) — The MessageSummary API from Listrak — 1 operation(s) for messagesummary.
- [Listrak Order API](https://apis.io/apis/listrak/listrak-order-api/) — The Order API from Listrak — 1 operation(s) for order.
- [Listrak PhoneList API](https://apis.io/apis/listrak/listrak-phonelist-api/) — The PhoneList API from Listrak — 2 operation(s) for phonelist.
- [Listrak Product API](https://apis.io/apis/listrak/listrak-product-api/) — The Product API from Listrak — 1 operation(s) for product.
- [Listrak RatingSummary API](https://apis.io/apis/listrak/listrak-ratingsummary-api/) — The RatingSummary API from Listrak — 1 operation(s) for ratingsummary.
- [Listrak Review API](https://apis.io/apis/listrak/listrak-review-api/) — The Review API from Listrak — 1 operation(s) for review.
- [Listrak SavedAudience API](https://apis.io/apis/listrak/listrak-savedaudience-api/) — The SavedAudience API from Listrak — 1 operation(s) for savedaudience.
- [Listrak SavedMessage API](https://apis.io/apis/listrak/listrak-savedmessage-api/) — The SavedMessage API from Listrak — 3 operation(s) for savedmessage.
- [Listrak Segmentation API](https://apis.io/apis/listrak/listrak-segmentation-api/) — The Segmentation API from Listrak — 2 operation(s) for segmentation.
- [Listrak SegmentationField API](https://apis.io/apis/listrak/listrak-segmentationfield-api/) — The SegmentationField API from Listrak — 2 operation(s) for segmentationfield.
- [Listrak SegmentationFieldGroup API](https://apis.io/apis/listrak/listrak-segmentationfieldgroup-api/) — The SegmentationFieldGroup API from Listrak — 2 operation(s) for segmentationfieldgroup.
- [Listrak Send API](https://apis.io/apis/listrak/listrak-send-api/) — The Send API from Listrak — 1 operation(s) for send.
- [Listrak SenderCode API](https://apis.io/apis/listrak/listrak-sendercode-api/) — The SenderCode API from Listrak — 2 operation(s) for sendercode.
- [Listrak Tickets API](https://apis.io/apis/listrak/listrak-tickets-api/) — The Tickets API from Listrak — 1 operation(s) for tickets.
- [Listrak TransactionalMessage API](https://apis.io/apis/listrak/listrak-transactionalmessage-api/) — The TransactionalMessage API from Listrak — 6 operation(s) for transactionalmessage.
- [Listrak TransactionalMessageActivity API](https://apis.io/apis/listrak/listrak-transactionalmessageactivity-api/) — The TransactionalMessageActivity API from Listrak — 1 operation(s) for transactionalmessageactivity.
- [Listrak TransactionalMessageResend API](https://apis.io/apis/listrak/listrak-transactionalmessageresend-api/) — The TransactionalMessageResend API from Listrak — 1 operation(s) for transactionalmessageresend.
- [Listrak Directories API](https://apis.io/apis/listrak/listrak-directories-api/) — The Directories API from Listrak — 2 operation(s) for directories.
- [Listrak Files API](https://apis.io/apis/listrak/listrak-files-api/) — The Files API from Listrak — 2 operation(s) for files.
- [Listrak Fonts API](https://apis.io/apis/listrak/listrak-fonts-api/) — The Fonts API from Listrak — 1 operation(s) for fonts.
- [Listrak Event Configurations API](https://apis.io/apis/listrak/listrak-event-configurations-api/) — REST endpoints to manage Custom Event Configurations.
- [Listrak IP Pool API](https://apis.io/apis/listrak/listrak-ip-pool-api/) — The IpPool resource exposes all of the IP Pools and their IDs for a user's Account.
- [Listrak List Import API](https://apis.io/apis/listrak/listrak-list-import-api/) — The List Import resource is used to supply an import file in order to import data to a list.
- [Listrak Split Test API](https://apis.io/apis/listrak/listrak-split-test-api/) — The SplitTest resource is used to retrieve information about automated email split tests.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Listrak Webhooks](https://apis.io/asyncapis/listrak/listrak-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [listrak](https://apis.io/servers/listrak/listrak/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Listrak Agentic Access](https://apis.io/agentic-access/listrak/listrak-agentic-access/)

#### JSON Schema (7)

The data models the API reads and writes.

- [Listrak Crosschannel API Schemas](https://apis.io/schemas/listrak/listrak-crosschannel-schemas/)
- [Listrak Data API Schemas](https://apis.io/schemas/listrak/listrak-data-schemas/)
- [Listrak Email API Schemas](https://apis.io/schemas/listrak/listrak-email-schemas/)
- [Listrak Mobileclient API Schemas](https://apis.io/schemas/listrak/listrak-mobileclient-schemas/)
- [Listrak Privacy API Schemas](https://apis.io/schemas/listrak/listrak-privacy-schemas/)
- [Listrak Sms API Schemas](https://apis.io/schemas/listrak/listrak-sms-schemas/)
- [Listrak Twowaysms API Schemas](https://apis.io/schemas/listrak/listrak-twowaysms-schemas/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Listrak Context](https://apis.io/jsonld/listrak/listrak-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Listrak Vocabulary](https://apis.io/vocabularies/listrak/listrak-vocabulary/)

#### Examples (4)

Example requests and responses.

- [Listrak Crosschannel_Event Example](https://apis.io/examples/listrak/listrak-crosschannel_event-example/)
- [Listrak Data_Order Example](https://apis.io/examples/listrak/listrak-data_order-example/)
- [Listrak Email_Contact Example](https://apis.io/examples/listrak/listrak-email_contact-example/)
- [Listrak Sms_Subscriber Example](https://apis.io/examples/listrak/listrak-sms_subscriber-example/)

#### Collections (52)

Postman and Open Collection request collections.

- [Listrak Cross Channel REST app-push-mobile-client-device API](https://apis.io/collections/listrak/open-listrak-app-push-mobile-client-device-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device app-push-mobile-client-engagements API](https://apis.io/collections/listrak/open-listrak-app-push-mobile-client-engagements-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device BroadcastMessage API](https://apis.io/collections/listrak/open-listrak-broadcastmessage-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device Campaign API](https://apis.io/collections/listrak/open-listrak-campaign-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device Contact API](https://apis.io/collections/listrak/open-listrak-contact-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device ContactListSubscription API](https://apis.io/collections/listrak/open-listrak-contactlistsubscription-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device ContactSegmentationField API](https://apis.io/collections/listrak/open-listrak-contactsegmentationfield-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device Content API](https://apis.io/collections/listrak/open-listrak-content-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device ContentFolder API](https://apis.io/collections/listrak/open-listrak-contentfolder-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device Conversation API](https://apis.io/collections/listrak/open-listrak-conversation-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device ConversationMessage API](https://apis.io/collections/listrak/open-listrak-conversationmessage-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device ConversationMessageActivity API](https://apis.io/collections/listrak/open-listrak-conversationmessageactivity-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device ConversationMessageLink API](https://apis.io/collections/listrak/open-listrak-conversationmessagelink-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device ConversationMessageLinkClicker API](https://apis.io/collections/listrak/open-listrak-conversationmessagelinkclicker-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device ConversationMessageSummary API](https://apis.io/collections/listrak/open-listrak-conversationmessagesummary-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device ConversationSummary API](https://apis.io/collections/listrak/open-listrak-conversationsummary-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device Customer API](https://apis.io/collections/listrak/open-listrak-customer-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device Event API](https://apis.io/collections/listrak/open-listrak-event-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device EventConfigurations API](https://apis.io/collections/listrak/open-listrak-eventconfigurations-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device EventGroup API](https://apis.io/collections/listrak/open-listrak-eventgroup-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device Events API](https://apis.io/collections/listrak/open-listrak-events-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device Folder API](https://apis.io/collections/listrak/open-listrak-folder-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device Forget API](https://apis.io/collections/listrak/open-listrak-forget-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device IpPool API](https://apis.io/collections/listrak/open-listrak-ippool-api/)
- [Listrak Cross Channel REST app-push-mobile-client-device List API](https://apis.io/collections/listrak/open-listrak-list-api/)
- …and 27 more published on APIs.io

#### Overlays (57)

OpenAPI overlays, including conversational phrasing for each operation.

- [Listrak App Push Mobile Client Device Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-app-push-mobile-client-device-api-phrasing-overlay/)
- [Listrak App Push Mobile Client Engagements Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-app-push-mobile-client-engagements-api-phrasing-overlay/)
- [Listrak Broadcastmessage Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-broadcastmessage-api-phrasing-overlay/)
- [Listrak Campaign Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-campaign-api-phrasing-overlay/)
- [Listrak Contact Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-contact-api-phrasing-overlay/)
- [Listrak Contactlistsubscription Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-contactlistsubscription-api-phrasing-overlay/)
- [Listrak Contactsegmentationfield Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-contactsegmentationfield-api-phrasing-overlay/)
- [Listrak Content Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-content-api-phrasing-overlay/)
- [Listrak Contentfolder Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-contentfolder-api-phrasing-overlay/)
- [Listrak Conversation Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-conversation-api-phrasing-overlay/)
- [Listrak Conversationmessage Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-conversationmessage-api-phrasing-overlay/)
- [Listrak Conversationmessageactivity Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-conversationmessageactivity-api-phrasing-overlay/)
- [Listrak Conversationmessagelink Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-conversationmessagelink-api-phrasing-overlay/)
- [Listrak Conversationmessagelinkclicker Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-conversationmessagelinkclicker-api-phrasing-overlay/)
- [Listrak Conversationmessagesummary Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-conversationmessagesummary-api-phrasing-overlay/)
- [Listrak Conversationsummary Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-conversationsummary-api-phrasing-overlay/)
- [Listrak Customer Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-customer-api-phrasing-overlay/)
- [Listrak Directories Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-directories-api-phrasing-overlay/)
- [Listrak Event Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-event-api-phrasing-overlay/)
- [Listrak Event Configurations Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-event-configurations-api-phrasing-overlay/)
- [Listrak Eventgroup Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-eventgroup-api-phrasing-overlay/)
- [Listrak Events Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-events-api-phrasing-overlay/)
- [Listrak Files Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-files-api-phrasing-overlay/)
- [Listrak Folder Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-folder-api-phrasing-overlay/)
- [Listrak Fonts Api Phrasing Overlay](https://apis.io/overlays/listrak/listrak-fonts-api-phrasing-overlay/)
- …and 32 more published on APIs.io

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [Listrak — jsonschema rules](https://apis.io/rules/listrak/listrak-jsonschema-spectral-rules/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Listrak Authentication](https://apis.io/security/listrak/listrak-authentication/)
- [Listrak Domain Security](https://apis.io/security/listrak/listrak-domain-security/)
- [Listrak Trust Center](https://apis.io/security/listrak/listrak-trust-center/)
- [Listrak Vulnerability Disclosure](https://apis.io/security/listrak/listrak-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Listrak Scopes](https://apis.io/scopes/listrak/listrak-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Listrak Plans Pricing](https://apis.io/plans/listrak/listrak-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Listrak Rate Limits](https://apis.io/rate-limits/listrak/listrak-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Listrak Finops](https://apis.io/finops/listrak/listrak-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.listrak.com/)
- [Documentation](https://www.listrak.com/learn/developers)
- [Getting started](https://help.listrak.com/en/articles/9406951-rest-api-integrations-at-listrak)
- [API reference](https://api.listrak.com/email)
- [Pricing](https://www.listrak.com/)
- [Sign up](https://www.listrak.com/get-started)
- [Support](https://help.listrak.com/en/)
- [Blog](https://www.listrak.com/learn/blog)
- [Security](https://www.listrak.com/privacy-and-terms/responsible-disclosure)
- [Compliance](https://www.listrak.com/privacy-and-terms/privacy-policy)
- [Terms of service](https://www.listrak.com/privacy-and-terms/acceptable-use-policy)
- [Privacy policy](https://www.listrak.com/privacy-and-terms/privacy-policy)
- [GitHub](https://github.com/listrak)
- [Status](https://status.listrak.com)

## API Evangelist rating

**Kin Score 72.7** — exemplar · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 71.4 |
| Contract quality | 66.7 |
| Contract governance | 28.0 |
| Operational transparency | 84.2 |
| Developer ergonomics | 60.1 |
| Access clarity | 81.6 |

**Agent readiness 35.9** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 44.2** — Telecommunications

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/listrak/](https://apis.io/providers/listrak/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Listrak: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/listrak/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
