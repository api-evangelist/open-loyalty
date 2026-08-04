# Open Loyalty (open-loyalty)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Open Loyalty is an API-first, headless loyalty and gamification platform. Every loyalty mechanic - members (customers), transactions, points, tiers/levels, earning rules, reward campaigns, and analytics - is exposed through a documented REST API, so brands build custom loyalty experiences on top of Open Loyalty rather than a fixed UI. The platform grew from an open-source loyalty engine (still available as a GitHub Open Source Edition, Apache-2.0, capped at ~200 members for testing) into a managed, cloud-hosted SaaS.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/open-loyalty/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/open-loyalty/refs/heads/main/apis.yml)

## Access Model (be honest)

- **Public API status:** Open Loyalty publishes a full, public REST API reference at [docs.openloyalty.io](https://docs.openloyalty.io/en/latest/api/) plus an interactive reference at [apidocs.openloyalty.io](https://apidocs.openloyalty.io/). The API is real and documented in detail, but you exercise it against **your own provisioned tenant instance** - Open Loyalty is per-tenant cloud SaaS, so there is no single shared public base host. The base URLs in this catalog use a `your-instance.openloyalty.io` template that you substitute with your tenant host (or `localhost` for a self-hosted Open Source Edition).
- **Authentication:** JWT bearer token obtained from `POST /admin/login_check` (admin) or `POST /{storeCode}/customer/login_check` (member), or a permanent `X-AUTH-TOKEN` API token. The overview docs also mention OAuth 2.0 as a supported pattern, but the concrete documented login flow is JWT.
- **Store scoping:** Almost every endpoint is scoped to a store via a `storeCode` path segment, e.g. `/api/<storeCode>/customer`.
- **Open source vs cloud:** The GitHub Open Source Edition ([github.com/OpenLoyalty](https://github.com/OpenLoyalty)) is self-hostable but limited to ~200 members, has no guaranteed performance/scalability, and is meant for testing. Production is the managed cloud SaaS, sold contact-sales and billed on Monthly Active Members.
- **Events:** Asynchronous notifications are delivered via outbound HTTP webhook callbacks (not a WebSocket). See `review.yml`.

## Tags

- Loyalty
- Gamification
- Rewards
- Points
- Loyalty Program
- Customer Engagement
- Headless
- API First

## Timestamps

- **Created:** 2026-07-10
- **Modified:** 2026-07-10

## APIs

### Open Loyalty Customer API

Register, list, read, and update loyalty members (customers), check existence by email or phone, manage activation and status, assign members to levels and POS, and read per-member history.

- **Human URL:** [https://docs.openloyalty.io/en/latest/api/customer.html](https://docs.openloyalty.io/en/latest/api/customer.html)
- **Base URL:** `https://your-instance.openloyalty.io/api`

### Open Loyalty Transactions API

Register purchase transactions, simulate the points a transaction would earn before committing, list and read transactions, assign transactions to members, import in bulk, and manage item labels.

- **Human URL:** [https://docs.openloyalty.io/en/latest/api/transactions.html](https://docs.openloyalty.io/en/latest/api/transactions.html)
- **Base URL:** `https://your-instance.openloyalty.io/api`

### Open Loyalty Points Transfers API

Award (add) and spend points, transfer points peer-to-peer between members, and cancel, activate, expire, or block a points transfer. The ledger surface for the loyalty points economy.

- **Human URL:** [https://docs.openloyalty.io/en/latest/api/points_transfers.html](https://docs.openloyalty.io/en/latest/api/points_transfers.html)
- **Base URL:** `https://your-instance.openloyalty.io/api`

### Open Loyalty Reward Campaigns API

Create and manage reward campaigns (the redeemable rewards catalog), toggle campaigns active, list active and publicly available campaigns, buy a reward campaign for a member, redeem/simulate cashback, and manage coupons and campaign media.

- **Human URL:** [https://docs.openloyalty.io/en/latest/api/campaign.html](https://docs.openloyalty.io/en/latest/api/campaign.html)
- **Base URL:** `https://your-instance.openloyalty.io/api`

### Open Loyalty Levels API

Create, list, read, update, activate, and delete loyalty tiers (levels), list the members assigned to a level, and manage level images.

- **Human URL:** [https://docs.openloyalty.io/en/latest/api/level.html](https://docs.openloyalty.io/en/latest/api/level.html)
- **Base URL:** `https://your-instance.openloyalty.io/api`

### Open Loyalty Earning Rules API

Create, list, read, update, and activate the earning rules that define how members earn points - purchase-based, event-based, QR code scans, and geolocation check-ins.

- **Human URL:** [https://docs.openloyalty.io/en/latest/api/earning_rule.html](https://docs.openloyalty.io/en/latest/api/earning_rule.html)
- **Base URL:** `https://your-instance.openloyalty.io/api`

## Common Properties

- [GitHub Organization](https://github.com/OpenLoyalty)
- [LinkedIn](https://www.linkedin.com/company/openloyalty)
- [Website](https://www.openloyalty.io)
- [Documentation](https://docs.openloyalty.io/en/latest/api/)
- [Plans](plans/open-loyalty-plans-pricing.yml)
- [Rate Limits](rate-limits/open-loyalty-rate-limits.yml)
- [Fin Ops](finops/open-loyalty-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
