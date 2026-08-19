---
name: independence-blue-cross-check-drug-coverage
description: >-
  Check whether a medication is on the Independence Blue Cross covered drug list, what tier it sits on,
  and whether it needs prior authorization or step therapy — using the public Da Vinci US Drug
  Formulary FHIR API. No authentication required.
generated: '2026-08-15'
method: generated
source: openapi/independence-blue-cross-formulary-api-openapi.yml
api: Independence Blue Cross Drug Formulary API
base_url: https://eapics.ibx.com/formulary/v1/fhir
auth: none
operations:
  - get_MedicationKnowledge
  - get_MedicationKnowledge_rid
  - get_List
  - get_List_rid
---

# Check Independence Blue Cross drug coverage

The Drug Formulary API is a **public, unauthenticated** HL7 FHIR R4 server implementing the Da Vinci
US Drug Formulary (USDF) implementation guide. Two resource types, four operations, all GET.

**Base URL:** `https://eapics.ibx.com/formulary/v1/fhir`
**Accept:** `application/fhir+json`

## The two resources

| Resource | What it is |
|---|---|
| `MedicationKnowledge` | One covered drug: its codes, its tier, and its coverage restrictions |
| `List` | A formulary — the set of drugs attached to a plan |

## Steps

### 1. Find the drug

```
GET /MedicationKnowledge?code={rxnorm-or-ndc-code}
```
Operation: `get_MedicationKnowledge`. Search by drug code rather than by brand name where you can —
codes are unambiguous and they are the join key to every other system.

### 2. Read the coverage detail

```
GET /MedicationKnowledge/{id}
```
Operation: `get_MedicationKnowledge_rid`.

Under the USDF profile the answers you want live in:

- `drugTierID` — the cost-sharing tier
- `priorAuthorization` — whether the plan requires PA before it will pay
- `stepTherapyLimit` — whether cheaper alternatives must be tried first
- `quantityLimit` — dispensing quantity restrictions

Read these from the returned resource; do not assume a default. A drug being present in the formulary
is not the same as a drug being unrestricted.

### 3. Confirm which formulary you are reading

```
GET /List?_count=50          # get_List
GET /List/{id}               # get_List_rid
```
`List.entry[].item` references the `MedicationKnowledge` records in that formulary. Coverage is
per-plan: a drug on one Independence formulary may not be on another, so resolve the member's plan
formulary before answering a coverage question definitively.

## Paging

Follow `Bundle.link[]` where `relation == "next"` verbatim. Use `_count` to request a page size.

## Errors

FHIR `OperationOutcome` in `application/fhir+json` — not RFC 9457. Statuses declared by the contract
are 400, 401, 403 and 404; on this public API you should only realistically see 400 and 404.

## Cautions

- **This is not a benefits quote.** The formulary tells you what the plan covers in general. It does
  not tell you a specific member's cost, deductible status or accumulator position. Do not present a
  tier as a price.
- `MedicationKnowledge` ids on this base share no id space with `Medication` on `patient/v1/fhir`.
  Join the two surfaces on drug code (RxNorm/NDC), never on logical id.
- The formulary base's own `.well-known/smart-configuration` document points at **AmeriHealth**
  authorization endpoints (`member.amerihealth.com`, `eapics.amerihealth.com`) — a shared-platform
  artifact between the two Independence Health Group brands. It does not matter here because the
  formulary needs no token, but do not follow it to authenticate against IBX.

## Rate limits

None published. Cache formulary results; this data changes on a monthly-ish cadence, not per request.
