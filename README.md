# Wyzant (wyzant)

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
