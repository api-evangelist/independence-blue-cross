---
name: independence-blue-cross-find-in-network-provider
description: >-
  Find an in-network Independence Blue Cross clinician, the practice they work for, and the address and
  hours you can see them at — using the public Da Vinci Plan-Net FHIR Provider Directory. No
  authentication and no member consent is required, so this is the safest IBX surface for an agent.
generated: '2026-08-15'
method: generated
source: openapi/independence-blue-cross-provider-directory-api-openapi.yml
api: Independence Blue Cross Provider Directory API
base_url: https://eapics.ibx.com/provider/v1/fhir
auth: none
operations:
  - get_Practitioner
  - get_Practitioner_rid
  - get_PractitionerRole
  - get_Organization
  - get_Organization_rid
  - get_Location
  - get_Location_rid
  - get_HealthcareService
---

# Find an in-network Independence Blue Cross provider

The Provider Directory is a **public, unauthenticated** HL7 FHIR R4 server implementing the Da Vinci
PDex Plan-Net implementation guide. Every operation is a GET. Nothing you do here can change state and
nothing here is protected health information.

**Base URL:** `https://eapics.ibx.com/provider/v1/fhir`
**Accept:** `application/fhir+json`

> Use this base, not `patient/v1/fhir`. The two bases both expose `Practitioner`, `Organization`,
> `PractitionerRole` and `Location`, but only this one carries the full directory record, and logical
> ids are **not** shared between them.

## Steps

### 1. Search for the clinician

```
GET /Practitioner?name=Smith
```
Operation: `get_Practitioner`. Other useful search parameters are `identifier` (use the NPI, which is
the only identifier that reliably crosses surfaces), `family`, `given` and `_id`.

The response is a FHIR `Bundle` of type `searchset`. Read `entry[].resource` for the matches and
`total` for the count.

### 2. Resolve where they actually practise

A bare `Practitioner` tells you who someone is, not where they work or whether they are in your
network. That lives in `PractitionerRole`.

```
GET /PractitionerRole?practitioner=Practitioner/{id}&_include=PractitionerRole:organization&_include=PractitionerRole:location
```
Operation: `get_PractitionerRole`. The `_include` parameters hydrate the referenced `Organization` and
`Location` in the same Bundle, which avoids an N+1 walk. Each included resource appears in
`entry[]` with `search.mode` of `include`.

### 3. Read the practice and the address

```
GET /Organization/{id}      # get_Organization_rid
GET /Location/{id}          # get_Location_rid
```
`Location` carries `address`, `position` (lat/long) and `hoursOfOperation`. `Organization.partOf`
points at a parent organization when the practice belongs to a larger system.

### 4. Check what the location actually offers

```
GET /HealthcareService?location=Location/{id}
```
Operation: `get_HealthcareService`.

## Paging

Never build page URLs by hand. Request a page size with `_count`, then follow the link the server
hands back:

```
Bundle.link[] where relation == "next"  ->  follow link.url verbatim
```

## Errors

Non-2xx responses carry a FHIR `OperationOutcome` in `application/fhir+json`, **not** RFC 9457
`application/problem+json`. Read `issue[].code` (an HL7 IssueType) and `issue[].diagnostics`.

| Status | What it usually means | What to do |
|---|---|---|
| 400 | Unsupported search parameter or modifier | Fix the parameter; do not retry unchanged |
| 404 | Wrong base path, or the id does not exist | Confirm you are on `provider/v1/fhir` |

`GET /metadata` returned HTTP 400 to anonymous requests when this skill was written, so do not depend
on the CapabilityStatement to discover search parameters — start from a resource search.

## Rate limits

None are published. The Developer Portal Terms and Conditions state limits exist but name no number,
no `RateLimit-*` header and no 429 response. Cache aggressively: directory data is reference data that
changes slowly, and you cannot detect throttling from the contract.

## Cautions

- Do not treat a `Practitioner` logical id from this base as valid on `patient/v1/fhir`. Match on NPI.
- Network participation is expressed through `PractitionerRole` and `InsurancePlan.coverage.network`.
  A `Practitioner` existing in the directory is not by itself proof of in-network status for a
  specific plan.
