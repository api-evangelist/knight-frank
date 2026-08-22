# Knight Frank (knight-frank)

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

Knight Frank LLP is a London-headquartered global real estate consultancy founded in 1896, structured as a partnership rather than a listed company, operating through a network of over 700 offices in more than 50 territories. It is best known for prime and super-prime residential agency, commercial agency and occupier services, valuation and advisory, capital markets, rural and agricultural consultancy, and the Knight Frank Research programme that publishes The Wealth Report and the Prime International Residential Index. Its home market is the United Kingdom, where there is no MLS and no cooperative listing standard — residential stock reaches consumers through the Rightmove and Zoopla duopoly by way of agency CRM software (Reapit, Alto, Street, Apex27) rather than a shared cooperative pool. Knight Frank is a supplier into that pipe, not an operator of it.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/knight-frank/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/knight-frank/refs/heads/main/apis.yml)

## Tags

- Real Estate
- United Kingdom
- Property Listings
- Commercial Real Estate
- Valuation
- Brokerage
- Property Management
- Rentals
- PropTech
- Research

## Timestamps

- **Created:** 2026-07-26
- **Modified:** 2026-07-26

## APIs

Knight Frank publishes **no developer programme at all** — and simultaneously runs **one API that answers anonymously**, with a live Swagger UI and a valid OpenAPI 3.0.1 document, to anybody who finds the hostname. These are two separate facts and neither implies the other.

### KnightFrank Api v3

The corporate search service behind `knightfrank.com` and `knightfrank.co.uk`, titled "KnightFrank Api v3" by its own OpenAPI document. Eleven operations across seven tags — CMSPage, IntelligenceLab, Office, Person, Search, ServiceLine and Telemetry — covering CMS content search, the Knight Frank Intelligence Lab research index, the global office directory, the people/partner directory with autocomplete, cross-site search, service-line lookup and a selection-count telemetry write.

- **Human URL:** [https://api-v3.web.prd-knightfrank.com/swagger/index.html](https://api-v3.web.prd-knightfrank.com/swagger/index.html)
- **Base URL:** `https://api-v3.web.prd-knightfrank.com`

#### Tags

- Search
- Directory
- Research
- Real Estate
- United Kingdom

#### Properties

- [OpenAPI](openapi/knight-frank-api-v3-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [API Reference](https://api-v3.web.prd-knightfrank.com/swagger/index.html)
- [Swagger JSON](https://api-v3.web.prd-knightfrank.com/swagger/v1/swagger.json)
- [Swagger YAML](https://api-v3.web.prd-knightfrank.com/swagger/v1/swagger.yaml)

This is **not** a published developer product. Knight Frank advertises it nowhere, documents it in no human-facing place, and offers no terms, keys or signup for it. It is listed here because it is a genuine, verifiable machine-readable contract that is reachable anonymously — probed on 2026-07-26, `/swagger/index.html` returned HTTP 200 with a working Swagger UI, `/swagger/v1/swagger.json` returned HTTP 200 with a valid OpenAPI 3.0.1 document (11,073 bytes), and `GET /office` and `GET /person` returned HTTP 200 with real office and staff records to a client presenting no credential of any kind. The document declares no `securitySchemes` and no authentication is enforced.

## What Was Probed And Failed

- `developer.knightfrank.com`, `developers.knightfrank.com`, `docs.knightfrank.com`, `apis.knightfrank.com`, `search.knightfrank.com` and `status.knightfrank.com` do not resolve in DNS.
- `api.knightfrank.com` resolves via Gcore but is answered by a WAF (`wswaf`) returning HTTP 502/503. No routes, no docs, no spec.
- `/developers`, `/api`, `/docs`, `/openapi.json`, `/swagger.json`, `/api-docs`, `/.well-known/openid-configuration`, `/.well-known/security.txt`, `/.well-known/ai-plugin.json` and `/llms.txt` all return 404 on `knightfrank.com`.
- The 125 KB sitemap at `https://www.knightfrank.com/sitemap.xml` (HTTP 200, 610 `<loc>` entries) contains **zero** `developer`, `swagger`, `openapi` or `graphql` matches.

### The homonym trap

`https://www.knightfrank.co.uk/developers` returns HTTP 200 — but it 301s to `https://www.knightfrank.co.uk/commercial/solutions/developers-housebuilders`, a commercial advisory page for **property developers and housebuilders**. This is a real estate homonym, not a developer portal, and must not be scored as one.

### The closed half of the estate

The property search application carries an inline `kfsearchconfig` object naming its backing services. The half that matters is shut:

- `api-v2.web.prd-knightfrank.com` — property search, saved properties, saved searches, alerts, consumer account. `GET /properties/search` → **401**. `GET /secure/account` → **401**. Its `/swagger/v1/swagger.json` 302s to an ASP.NET error page; no contract is served.
- `api-v3.web.prd-knightfrank.com` — corporate site search. Open, as described above.

The data a real estate developer would actually want lives on v2, and v2 is gated.

## RESO Posture

**Not certified. No RESO reference found anywhere in the Knight Frank estate.**

The official RESO Certification Status list at [https://www.reso.org/certificates/](https://www.reso.org/certificates/) (HTTP 200, 416,233 bytes) was searched for "knight", "knight frank" and "knightfrank" — zero matches. It was also searched for "United Kingdom" and "England" — zero matches; every listed organization is United States based. `https://certification.reso.org/` returned HTTP 400 to an anonymous client and `https://www.reso.org/upi/` returned 404.

No OData `$metadata` document exists — probed on both `api-v3` and `api-v2`, both 404. The harvested contract is plain OpenAPI 3.0.1, not OData. No Universal Property Identifier appears anywhere; Knight Frank uses its own internal integer `officeId` and `empNo` identifiers.

> **False positive recorded:** a grep of `knightfrank.co.uk` matches the string `odata`. It is the substring of `"nodata"` inside an EPiServer/Optimizely Forms localization block. It is not an OData reference.

This is structural rather than a lapse. RESO is a North American NAR/MLS mechanism, the UK has no MLS to certify against, and Knight Frank's US arm (`knightfrank.us` → `knightfrank.com/usa`) is a commercial and prime-residential advisory operation, not a residential MLS participant.

## Access Gate

**`none-published`.** There is no developer signup, no application form, no partner or data-licence programme, no API terms of use, no sandbox and no key issuance process published anywhere on `knightfrank.com`, `knightfrank.co.uk` or any of the ~40 country domains. The only published route into a Knight Frank data conversation is the corporate contact form at [https://www.knightfrank.co.uk/contact-us](https://www.knightfrank.co.uk/contact-us). Classifying this as `partner-only` would imply a partner programme exists; none is published.

**Why the gate is still recorded as closed despite an anonymous endpoint.** The gate describes what Knight Frank *offers*, which is nothing. The listing and account data lives on `api-v2` behind Azure AD B2C and returns 401, with no documented path for a third party to register a client in that tenant. The surface that *is* anonymous — `api-v3` — is an internal corporate site-search service at a hostname (`web.prd-knightfrank.com`) that is plainly an internal environment naming convention, carrying no terms and no stability commitment. A developer can call it today. A developer has not been invited to.

## Open Data

**No.** Knight Frank publishes no open, unlicensed, publicly callable dataset. Knight Frank Research — The Wealth Report, PIRI 100, the Luxury Investment Index, the Wealth Sizing Model — ships as PDF reports and web narrative at [https://www.knightfrank.com/research](https://www.knightfrank.com/research) with no data download, no CSV, no feed and no API. The anonymously reachable `/intelligencelab` operations index that research output for site search, but a search index over marketing content behind an unadvertised internal endpoint is not published open data.

The genuinely open UK property layer sits in the public sector and is not operated by Knight Frank: **HM Land Registry** Price Paid Data and ownership data under the Open Government Licence, and **Ordnance Survey**'s addressing and mapping open products. This is the structural inverse of the United States — the UK has no industry standard and no MLS, but it does have real open government property APIs, and none of them come from the brokerages or the portals.

## Auth Model

Two surfaces, two answers:

- **`api-v3`** — **none**. The harvested OpenAPI document declares no `components.securitySchemes` and no `security` array, and live GETs succeeded with no credential.
- **`api-v2`** — **OAuth 2.0 / OpenID Connect via Azure AD B2C**, bearer token acquired through MSAL. Custom domain `login.prd-knightfrank.com`, tenant `KnightFrankB2Cprod.onmicrosoft.com` (`ea15e386-0dbc-4a5b-ac74-08f50f444486`), custom policy `B2C_1A_MYKFSIGNIN`, resource scope `MyKf.ReadWrite`.

Two OpenID Connect discovery documents were fetched anonymously (both HTTP 200) and saved verbatim:

- [`authentication/knight-frank-b2c-mykfsignin-openid-configuration.json`](authentication/knight-frank-b2c-mykfsignin-openid-configuration.json) — via the custom domain
- [`authentication/knight-frank-b2clogin-mykfsignin-openid-configuration.json`](authentication/knight-frank-b2clogin-mykfsignin-openid-configuration.json) — via `b2clogin.com`

Both advertise `scopes_supported: ["openid"]` only, `RS256`, `pairwise` subjects, and a custom claim `extension_HubContactId` linking a consumer account to an internal Knight Frank "Hub" CRM record. This is a **consumer** identity system for the "My Knight Frank" saved-property feature — an end-user login, not a developer credential.

No `security.txt` is published on either domain.

## Webhooks, Events, SDKs, Postman

Absence across the board, and that is the finding:

- **Webhooks:** none documented or referenced.
- **Events:** no event bus, no streaming, no AsyncAPI, no WebSocket. The only event-shaped operation is `POST /telemetry/increment-selected-count`, a client analytics write.
- **SDKs:** none. `https://github.com/knightfrank` returns 404. `https://github.com/knight-frank` returns 200 but the GitHub API reports it as type `User`, name null, created 2018-07-01, with **0 public repositories** — an unrelated empty personal handle, not the firm.
- **Postman:** no official collection or workspace.
- **Changelog / status page / rate limits / sandbox:** none.
- **`llms.txt` / `ai-plugin.json`:** neither exists. `robots.txt` on both domains blanket-disallows CCBot, Amazonbot, AMAZONAWS, awsbot, SemrushBot, SemrushBot-SA and rogerbot — a refusal is the only machine-access posture Knight Frank publishes.

## Common Properties

- [Website](https://www.knightfrank.com/)
- [Knight Frank United Kingdom](https://www.knightfrank.co.uk/)
- [Knight Frank United States](https://www.knightfrank.com/usa)
- [Property Search](https://www.knightfrank.co.uk/properties/residential/for-sale/london)
- [Research](https://www.knightfrank.com/research)
- [My Knight Frank Account](https://account.knightfrank.com/)
- [Contact](https://www.knightfrank.co.uk/contact-us)
- [Careers](https://www.knightfrank.com/recruitment)
- [LinkedIn](https://uk.linkedin.com/company/knight-frank)

## Review

The full probe trail — 74 recorded URLs with HTTP status, the harvested OpenAPI provenance, the live anonymous endpoint verification, the RESO evidence, the access gate, the open-data finding and the auth model — is in [review.yml](review.yml).

## Maintainers

- Kin Lane &lt;kin@apievangelist.com&gt;
