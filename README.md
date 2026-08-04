# Tithe.ly (tithely)

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

Tithe.ly is a church-technology platform for online and mobile giving, church management (ChMS), branded church apps, websites, events, and messaging. Its developer API lets churches and approved partners create donations, tokenize cards and bank accounts for PCI-safe payments, charge one-time and recurring gifts, manage giving funds (payment categories), and look up organizations.

**Access is gated.** The Tithe.ly API is granted **by request** to organizations that use (or are moving to) Tithe.ly. You email `support@tithe.ly`, describe what you want to build, and approved requesters receive **public and private API keys** by email. Integrators build and validate against a test environment (`tithelydev.com`) before promoting to the live environment (`tithe.ly`). Two generations are documented: a **V1** payments/tokenization API (Tithely.js plus charge endpoints) and a **V2** REST API (organizations, transactions, funds, and mail).

Because full field-level request/response schemas live behind the approved-partner developer docs, the OpenAPI in this entry documents the **publicly listed paths and methods** with **modeled** request and response bodies. See `review.yml` for the confirmed vs. modeled breakdown.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/tithely/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/tithely/refs/heads/main/apis.yml)

## Tags

- Church Giving
- Donations
- Fundraising
- Payments
- Nonprofit
- ChMS
- Faith

## Timestamps

- **Created:** 2026-07-03
- **Modified:** 2026-07-03

## Authentication

- **V2 REST API** (`https://tithe.ly/api/v2`): header `Authorization: {API_ID}:{API_TOKEN}`. The `POST /login` endpoint is the only V2 call that does not require the header.
- **V1 payments API** (`https://tithe.ly/api/v1`, test `https://tithelydev.com/api/v1`): uses the private key issued on approval; payment methods are created from tokens produced client-side by Tithely.js.

## APIs

### Tithe.ly Transactions API

Create donation transactions (one-time or recurring) against an organization and a payment category (fund) using a tokenized payment method.

- **Human URL:** [https://tithe.ly/api/v2/docs](https://tithe.ly/api/v2/docs)
- **Base URL:** `https://tithe.ly/api/v2`

### Tithe.ly Payments & Tokenization API

PCI-safe payment flow. Tithely.js renders a hosted iframe to tokenize a card or bank account client-side; the resulting token is attached to a user via `payment-methods` and charged with `charge` (repeat/recurring) or `charge-once` (one-time).

- **Human URL:** [https://docs.tithe.ly/reference/tokenization-with-tithelyjs-v2](https://docs.tithe.ly/reference/tokenization-with-tithelyjs-v2)
- **Base URL:** `https://tithe.ly/api/v1` (test `https://tithelydev.com/api/v1`)

### Tithe.ly Organizations API

Retrieve one or more Tithe.ly organizations (churches) by ID, and search organizations by owner.

- **Human URL:** [https://tithe.ly/api/v2/docs](https://tithe.ly/api/v2/docs)
- **Base URL:** `https://tithe.ly/api/v2`

### Tithe.ly Payment Categories (Funds) API

Create, read, and update payment categories - Tithe.ly's giving funds that donations are allocated to for a given organization.

- **Human URL:** [https://tithe.ly/api/v2/docs](https://tithe.ly/api/v2/docs)
- **Base URL:** `https://tithe.ly/api/v2`

### Tithe.ly Mail API

Send templated transactional emails (such as giving receipts and notifications) to recipients on behalf of an organization.

- **Human URL:** [https://tithe.ly/api/v2/docs](https://tithe.ly/api/v2/docs)
- **Base URL:** `https://tithe.ly/api/v2`

### Tithe.ly Accounts API

Authenticate a user and obtain the credentials used for subsequent V2 calls.

- **Human URL:** [https://tithe.ly/api/v2/docs](https://tithe.ly/api/v2/docs)
- **Base URL:** `https://tithe.ly/api/v2`

## Confirmed Endpoints

- `POST /api/v2/login`
- `GET  /api/v2/organization/{id}`
- `GET  /api/v2/organization-owner/{id}`
- `GET  /api/v2/payment_category/{id}`
- `POST /api/v2/payment_category`
- `PUT  /api/v2/payment_category/{id}`
- `POST /api/v2/transaction`
- `POST /api/v2/mail`
- `POST /api/v1/payment-methods`
- `POST /api/v1/charge`
- `POST /api/v1/charge-once`

## Pricing (summary)

Online giving has a free-forever plan (no monthly fee); churches pay per-transaction processing fees: ~2.9% + $0.30 (card), ~1% + $0.30 (ACH), ~3.5% + $0.30 (Amex). Donors can opt to cover fees. Software subscriptions (ChMS ~$72/mo, All-Access ~$119/mo) and Enterprise (custom) add fixed cost. The API itself has no separate metered price. Verify current rates at [get.tithe.ly/pricing](https://get.tithe.ly/pricing). See `plans/tithely-plans-pricing.yml`, `rate-limits/tithely-rate-limits.yml`, and `finops/tithely-finops.yml`.

## WebSocket Review

Does Tithe.ly expose a documented public WebSocket API? **No.** Tithe.ly's documented developer surface is request/response REST (V1 payments + V2 REST) plus the browser-side Tithely.js tokenization library. No WebSocket or public webhook/event-subscription surface is documented. See `review.yml`.

## Common Properties

- [GitHub Organization](https://github.com/tithely)
- [LinkedIn](https://www.linkedin.com/company/tithe-ly)
- [Website](https://get.tithe.ly/)
- [Documentation](https://docs.tithe.ly/reference/introduction)
- [Plans](plans/tithely-plans-pricing.yml)
- [Rate Limits](rate-limits/tithely-rate-limits.yml)
- [Fin Ops](finops/tithely-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
