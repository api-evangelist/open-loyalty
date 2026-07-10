# Open Loyalty (open-loyalty)

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
