---
name: independence-blue-cross-member-health-record-access
description: >-
  Retrieve an Independence Blue Cross member's own claims, coverage and clinical history through the
  CMS-mandated Patient Access API, using SMART on FHIR OAuth 2.0 with the member's explicit consent.
  This surface returns protected health information and must never be called without a member-authorized
  token.
generated: '2026-08-15'
method: generated
source: >-
  openapi/independence-blue-cross-patient-access-api-openapi.yml,
  openapi/_original/independence-blue-cross-patient-openapi.yml,
  https://eapics.ibx.com/patient/v1/fhir/.well-known/smart-configuration
api: Independence Blue Cross Patient Access API
base_url: https://eapics.ibx.com/patient/v1/fhir
auth: oauth2 / SMART App Launch 1.0.0
phi: true
operations:
  - get_Patient
  - get_Patient_rid
  - get_Coverage
  - get_ExplanationOfBenefit
  - get_ExplanationOfBenefit_rid
  - get_Condition
  - get_MedicationRequest
  - get_Observation
  - get_Immunization
  - get_Encounter
  - get_AllergyIntolerance
  - get_CarePlan
  - get_Procedure
  - get_DiagnosticReport
---

# Access an Independence Blue Cross member's health record

This API exists because CMS-9115-F requires it. It returns **protected health information** for one
member at a time, only with that member's consent, and only for members of Independence Medicare
Advantage or Keystone HMO CHIP plans. Medicare Supplement (Medigap) members are explicitly out of
scope and will not have data here.

**Base URL:** `https://eapics.ibx.com/patient/v1/fhir`
**Accept:** `application/fhir+json`

## Before you start

You need a registered application. Register the company and the member-facing app at
<https://devportal.ibx.com/cmssignin/>. Per the Developer Portal Terms and Conditions, credentials may
only be used with the application they were issued for — using them with another product is grounds
for revocation.

## 1. Authorize — SMART App Launch 1.0.0

Discovery (fetch this, do not hardcode):

```
GET https://eapics.ibx.com/patient/v1/fhir/.well-known/smart-configuration
```

As probed on 2026-08-15 it returns:

- `authorization_endpoint`: `https://member.ibx.com/patientaccesssvc/oauth2/v1/authorize`
- `token_endpoint`: `https://eapics.ibx.com/oauth2/v2/token`
- `capabilities`: `client-public`, `sso-openid-connect`, `launch-standalone`,
  `client-confidential-symmetric`, `context-standalone-patient`, `permission-offline`,
  `permission-patient`

Run the standalone authorization-code flow. `client-public` is advertised, so a public client **must**
use PKCE. Request the scopes the contract declares:

| Scope | Why |
|---|---|
| `launch/patient` | Standalone patient context |
| `patient/*.read` | Read the member's FHIR resources |
| `openid` | Member identity |
| `offline_access` | Refresh token, so you are not re-prompting the member |

Send the token as `Authorization: Bearer {access_token}`.

> Token lifetime is **not published** in the SMART configuration or anywhere else. Assume it is short,
> take `offline_access`, and refresh on 401 rather than on a timer you guessed.

## 2. Anchor on the patient

```
GET /Patient          # get_Patient
```
The token carries `context-standalone-patient`, so this resolves to exactly one member. Everything
below hangs off that Patient.

## 3. Pull coverage and claims

```
GET /Coverage                    # get_Coverage
GET /ExplanationOfBenefit        # get_ExplanationOfBenefit
GET /ExplanationOfBenefit/{id}   # get_ExplanationOfBenefit_rid
```

`ExplanationOfBenefit` is the substance of this API — adjudicated claims and encounter data from
capitated providers, shaped by the CARIN Blue Button framework and the Common Payer Consumer Data Set.
It references `Coverage` via `insurance.coverage`, the payer via `insurer`, and the rendering clinician
via `provider`.

## 4. Pull the clinical record

Each of these is a type-level search scoped to the member by the token:

```
GET /Condition            GET /Observation          GET /DiagnosticReport
GET /MedicationRequest    GET /Immunization         GET /AllergyIntolerance
GET /Encounter            GET /CarePlan             GET /Procedure
GET /Goal                 GET /Medication
```

Clinical resources follow US Core 3.1.1. Instance reads are available for each as
`GET /{Resource}/{id}`.

**Known gap:** `MedicationDispense` has an instance read (`get_MedicationDispense_rid`) but **no**
type-level search. You cannot enumerate dispenses — you can only dereference an id you obtained
elsewhere, typically from `MedicationRequest`.

## 5. Page through results

```
Bundle.link[] where relation == "next"  ->  follow url verbatim
```
Use `_count` for page size and `_include` / `_revinclude` to hydrate references in one round trip.

## Errors

FHIR `OperationOutcome` in `application/fhir+json`, not RFC 9457.

| Status | Meaning | Action |
|---|---|---|
| 400 | Bad search parameter | Fix the request; do not retry unchanged |
| 401 | Missing / expired token | Refresh via `offline_access`, or re-run the authorization flow |
| 403 | Outside patient context or scope, or consent revoked | Stop. Do not retry. Re-obtain consent |
| 404 | Unknown id or resource type not on this base | Confirm base path and id provenance |

No 429 and no 5xx are declared anywhere in the contract, and no `RateLimit-*` header is documented, so
you cannot distinguish throttling from a generic failure. Back off conservatively.

## Handling PHI — non-negotiable

- **Consent is revocable at any time.** The member can stop sharing whenever they choose. Treat a 403
  as a consent event, not a transient error, and stop polling.
- Only request the resources you need. `patient/*.read` is broad; scope your reads narrowly anyway.
- Never log, cache in plaintext, or forward this data outside the boundary the member consented to.
- Independence explicitly does not sell member health information to third parties and does not
  oversee your app's practices — the duty of care after the data leaves `eapics.ibx.com` is yours.
- These are read-only endpoints. There is no write surface, no idempotency key, and nothing here can
  change a member's record.
