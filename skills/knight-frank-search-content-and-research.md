---
name: Search Knight Frank content and research
description: Run a federated cross-site search, then drill into the Intelligence Lab research index, CMS pages and service-line taxonomy.
api: openapi/knight-frank-api-v3-openapi.json
base_url: https://api-v3.web.prd-knightfrank.com
operations:
  - GET /search
  - GET /intelligencelab
  - GET /intelligencelab/facets
  - GET /cmspage
  - GET /service-lines
operation_ids:
  - searchAll
  - searchIntelligenceLab
  - getIntelligenceLabFacets
  - searchCmsPages
  - searchServiceLines
operation_id_note: >-
  The harvested contract declares no operationIds. The ids above are assigned by
  overlays/knight-frank-api-v3-overlay.yaml; the method+path pairs are the real,
  verified surface.
generated: '2026-07-26'
method: generated
---

# Search Knight Frank content and research

Five real operations on the anonymous Knight Frank corporate search API (`api-v3`). This is the search layer behind knightfrank.com and knightfrank.co.uk — an Optimizely/EPiServer Find front end over Azure Cognitive Search.

## Before you start

- **No credential is required or accepted** (`authentication/knight-frank-authentication.yml`). No terms permit third-party use; there is no support channel and no stability commitment.
- **Property listings are not here.** `GET /search` returns a `propertiesAndSuggestions` array, but it comes back empty to anonymous callers — the property surface lives on `api-v2`, publishes no contract, and returns `401` without an Azure AD B2C consumer token.
- **Research is not data.** The Intelligence Lab index returns publication metadata (title, `publishedOn`, description, category) and links. The Wealth Report, PIRI 100 and the Luxury Investment Index ship as PDF and web narrative; there is no dataset, feed or download behind this API.

## Step 1 — federated search

```
GET https://api-v3.web.prd-knightfrank.com/search
    ?term=london
    &hostname=www.knightfrank.co.uk
    &languageCode=en
    &take=5
```

- The parameter is `term`. Passing `searchTerm` returns **HTTP 204 with an empty body** rather than a validation error — a silent failure mode worth guarding against.
- **The `people` facet is personal data.** It returns named individuals with corporate email, direct-dial and mobile to callers presenting no credential. Under UK GDPR the fact that the endpoint answers is not a lawful basis to collect, store or process what it returns. Do not page through it, do not persist it, and do not feed it to a model or a marketing list. This skill is for the content and research facets; the dedicated people-search operations are deliberately not packaged (see `_index.yml`).
- The response is a **composite object**, not a list: `diagnostics`, `propertiesAndSuggestions`, `people` + `peopleHasMore`, `offices` + `officeHasMore`, `research` + `researchHasMore`, `blog` + `blogHasMore`, `cms` + `cmsHasMore`, `serviceLines` + `serviceLinesHasMore`.
- Each hit is `{id, type, url, text, <typed payload>, diagnostics}` where `type` discriminates `people` / `offices` / `research` / `blog` / `cms` / `serviceLines`.
- There is no shared pagination block — each content type carries only its own `HasMore` boolean, with no per-type offset. To page a single type, switch to that type's own operation.

## Step 2 — drill into research

```
GET https://api-v3.web.prd-knightfrank.com/intelligencelab
    ?term=prime
    &languageCode=en
    &hostname=www.knightfrank.com
    &skip=0
    &take=10
```

- Returns the envelope `{results, hasMore, totalCount, fromFuzzySearch}`. Page by incrementing `skip` until `hasMore` is `false`.
- `fromFuzzySearch: true` means the exact query matched nothing and the service fell back to a fuzzy query — treat those results as weaker.
- Optional filters mirror the two enums the contract does declare: `searchFilterType` (`IntelligenceLabSearchFilterType`) and `orderBy` (`IntelligenceLabOrderBy`), plus `mediaType`, `dateRange` and `sourceType`.
- `GET /intelligencelab/facets` returns facet buckets for the same index. **Call it with the query parameters populated** — omitting them returned HTTP `500`, not a validation error, when probed.

## Step 3 — CMS pages and service lines

```
GET https://api-v3.web.prd-knightfrank.com/cmspage
    ?term=valuation&take=10&skip=0&languageCode=en&hostname=www.knightfrank.co.uk

GET https://api-v3.web.prd-knightfrank.com/service-lines
    ?term=valuation&isoCode=GB&domain=www.knightfrank.co.uk&languageCode=en
```

Both return the `{results, hasMore, totalCount, fromFuzzySearch}` envelope. Note `/service-lines` filters on **`domain`** while every other operation uses **`hostname`**.

## Error handling

The contract declares only `200 Success` on all five operations. In practice: `204` with an empty body for an unrecognised parameter name, `500` for missing required parameters, `404` with a zero-byte body for an unknown route. No `application/problem+json`, no error codes, no validation messages (`errors/knight-frank-error-responses.yml`).

## Idempotency and retries

All five operations are `GET` and safe to retry. Relevance ordering is not stable between calls, so do not treat result position as an identifier — key on the `id` field.
