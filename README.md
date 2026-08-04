# Wyzant (wyzant)

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

Wyzant is a US tutoring marketplace that connects students with independent tutors for in-person and online lessons across thousands of subjects. It is a consumer product, not a developer platform: students browse, book, message, and pay for lessons through wyzant.com, paying each tutor's hourly rate plus a Wyzant service fee (a percentage of the lesson cost). There is **no public REST API** for managing lessons, bookings, messages, or payments.

Wyzant does, however, expose a real **partner/affiliate data interface** at `data.wyzant.com` for approved affiliates (via Wyzant's ShareASale-based partner program). It offers a real-time **Tutor Search API** and a bulk **Tutor Data Feed**, both keyed by a per-partner API key and returning XML or JSON, so partners can surface Wyzant tutors on their own sites and earn a bounty per qualified student lead. Access requires an approved partner account; the API is not open to the general public.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/wyzant/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/wyzant/refs/heads/main/apis.yml)

## API Access Model

- **Consumer marketplace (wyzant.com):** No public API. All lesson booking, messaging, and payment happens in the product.
- **Partner / affiliate (data.wyzant.com):** Real, documented, partner-only. Requires an API key issued from the partner dashboard. Read-only tutor discovery (search + full feed).
- **Open source:** None. Wyzant is proprietary; there is no SDK or self-hostable component.
- **WebSocket / realtime:** None documented.

## Tags

- Tutoring
- Education
- Marketplace
- Tutors
- EdTech
- Affiliate
- Partner API
- Data Feed

## Timestamps

- **Created:** 2026-07-03
- **Modified:** 2026-07-03

## APIs

### Wyzant Tutor Search API

Real-time search against Wyzant's live tutor database for approved affiliates. An HTTP `POST` to `/api/search` with a partner API key and search parameters (`SearchString`, `ZIP`, `Distance`, `MinHourly`/`MaxHourly`, `MinAge`/`MaxAge`, gender, `MaxResults`) returns matching active tutors as XML or JSON, with fields such as tutor name, location, fee per hour, rating, subjects, and a tracked profile link.

- **Human URL:** [API & Data Feed Documentation](https://support.wyzant.com/hc/en-us/articles/115005857526-API-Data-Feed-Documentation)
- **Base URL:** `https://data.wyzant.com`

#### Tags

- Tutors
- Search
- Affiliate

#### Properties

- [Documentation](https://support.wyzant.com/hc/en-us/articles/115005857526-API-Data-Feed-Documentation)
- [API Reference](https://support.wyzant.com/hc/en-us/articles/115005857526-API-Data-Feed-Documentation)
- [OpenAPI](openapi/wyzant-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### Wyzant Tutor Data Feed

Bulk data feed that returns a complete snapshot of all active tutors listed on Wyzant at the time of the request. An HTTP `GET` to `/feeds/downloadFeed` with a partner API key and a `feedFormat` of XML or JSON (plus an optional `maxResults` for testing) downloads the full tutor dataset. Because the file is large, Wyzant asks partners to pull it at most once per day and to refresh a local copy at least weekly.

- **Human URL:** [API & Data Feed Documentation](https://support.wyzant.com/hc/en-us/articles/115005857526-API-Data-Feed-Documentation)
- **Base URL:** `https://data.wyzant.com`

#### Tags

- Tutors
- Data Feed
- Bulk Export

#### Properties

- [Documentation](https://support.wyzant.com/hc/en-us/articles/115005857526-API-Data-Feed-Documentation)
- [OpenAPI](openapi/wyzant-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/wyzant)
- [Website](https://www.wyzant.com)
- [Documentation](https://support.wyzant.com/hc/en-us/articles/115005857526-API-Data-Feed-Documentation)
- [Partner Program](https://highered.wyzant.com/partner)
- [Plans](plans/wyzant-plans-pricing.yml)
- [Rate Limits](rate-limits/wyzant-rate-limits.yml)
- [Fin Ops](finops/wyzant-finops.yml)

## Pricing

- **Students:** Pay each tutor's hourly rate (average roughly $35–$60/hour; range from about $15 up to $485/hour depending on subject and tutor) plus a Wyzant service fee charged as a percentage of the lesson cost (published around 9%). The first hour with a new tutor is covered by the Good Fit Guarantee.
- **Partners:** The Search API and Data Feed are free to approved affiliates; partners earn a bounty per qualified student lead (referenced publicly around $8 per lead; governed by the current partner agreement). Bounty payments are processed on the 15th of the month for the prior month.

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
