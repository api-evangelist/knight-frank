---
name: Find a Knight Frank office
description: Search the Knight Frank global office directory by term and country, then fetch the full record for one office by id.
api: openapi/knight-frank-api-v3-openapi.json
base_url: https://api-v3.web.prd-knightfrank.com
operations:
  - GET /office
  - GET /office/{id}
operation_ids:
  - searchOffices
  - getOfficeById
operation_id_note: >-
  The harvested contract declares no operationIds. The ids above are assigned by
  overlays/knight-frank-api-v3-overlay.yaml; the method+path pairs are the real,
  verified surface.
generated: '2026-07-26'
method: generated
---

# Find a Knight Frank office

Two real operations on the anonymous Knight Frank corporate search API (`api-v3`).

## Before you start

- **No credential is required or accepted.** The contract declares no `securitySchemes` and the host enforces no authentication (`authentication/knight-frank-authentication.yml`).
- **This is not a published developer product.** Knight Frank advertises no API, publishes no terms permitting third-party use, offers no support channel and makes no stability commitment. Verify you have a legitimate basis to call it before you do.
- **No rate-limit contract exists.** No `RateLimit`/`Retry-After` headers and no `429` were observed. Be conservative; the upstream `api.knightfrank.com` edge WAF drops clients that hammer it.

## Step 1 — search the directory

```
GET https://api-v3.web.prd-knightfrank.com/office
    ?term=london
    &isoCode=GB
    &languageCode=en
    &maxResultCount=5
```

- `term` is the search string; `isoCode` filters by country (ISO 3166-1 alpha-2); `maxResultCount` is the page size on this operation (**not** `take` — the parameter names differ per operation, see `conventions/knight-frank-conventions.yml`).
- The response is a **bare JSON array** with no envelope, no `totalCount` and no `hasMore`. You cannot tell from the response whether more results exist.
- Each record carries `officeId`, `name`, `address1`–`address5`, `postcode`, `country`, `countryCode`, `phoneNumber`, `emailAddress`, `url`, `officeOpeningTimes` and a `geoLocation` object with `coordinates`, `longitude` and `latitude`. The Azure Cognitive Search relevance value leaks through as `@search.score` — ordering is relevance-based, not stable.

## Step 2 — fetch the full office record

```
GET https://api-v3.web.prd-knightfrank.com/office/{id}?languageCode=en
```

- `{id}` is the integer `officeId` from step 1 (e.g. `1976`).
- The response is the office **object directly** — a third envelope shape in the same API.

## Error handling

The contract declares only `200 Success` on both operations. In practice (`errors/knight-frank-error-responses.yml`):

- An unknown route returns `404` with a **zero-byte body** and no content type.
- Omitting parameters other operations require can produce an unstructured `500` rather than a `400`.
- A misspelled parameter name is silently ignored rather than rejected.

Do not expect `application/problem+json`, an error code, or any machine-readable failure signal — there is none.

## Idempotency and retries

Both operations are `GET` and therefore safe to retry. There is **no** `Idempotency-Key` mechanism anywhere in this API; do not assume replay protection on the one write operation (`POST /telemetry/increment-selected-count`), which is not part of this skill.
