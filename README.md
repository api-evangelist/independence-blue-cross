# Independence Blue Cross

Independence Blue Cross (IBX) is the Blue Cross Blue Shield Association licensee for southeastern Pennsylvania (Bucks, Chester, Delaware, Montgomery, and Philadelphia counties) and a subsidiary of Independence Health Group, Inc., the 2013 holding company that also owns the AmeriHealth commercial brands (including AmeriHealth New Jersey and AmeriHealth Administrators TPA) and majority-owns the AmeriHealth Caritas family of Medicaid managed-care plans. IBX has called Philadelphia home for more than 85 years, serves nearly three million members directly, and — through Independence Health Group — supports roughly nine million covered lives across commercial, Medicare Advantage, Medicaid, CHIP, dental, vision, and behavioral health lines of business. Independence Health Group reported consolidated revenue of $36.3 billion for 2025.

To satisfy the CMS Interoperability and Patient Access final rule (CMS-9115-F), Independence Blue Cross publishes three HL7 FHIR R4 (4.0.1) APIs from a single shared gateway at `https://eapics.ibx.com`, documented through the developer portal at `https://devportal.ibx.com/`.

## APIs

| API | Base URL | Auth | Implementation Guide |
| --- | --- | --- | --- |
| Patient Access FHIR API | `https://eapics.ibx.com/patient/v1/fhir` | SMART on FHIR / OAuth 2.0 with PKCE | US Core 3.1.1, CARIN BB, Da Vinci PDex |
| Provider Directory FHIR API | `https://eapics.ibx.com/provider/v1/fhir` | None (public) | Da Vinci PDex Plan-Net |
| Drug Formulary FHIR API | `https://eapics.ibx.com/formulary/v1/fhir` | None (public) | Da Vinci US Drug Formulary (USDF) |
| Transparency in Coverage MRFs | `https://www.ibx.com/cmstic/?brand={khpe\|qcc\|iac}` | None (public bulk download) | 45 CFR Part 147.211 |

Population scope for the Patient Access API per the developer portal: **Independence Medicare Advantage (MA) and Keystone HMO Children's Health Insurance Program (CHIP) members**. Commercial / group populations are out of scope on this surface; Medicaid populations served by the AmeriHealth Caritas family of plans live on the separate `developer.amerihealthcaritas.com` portal.

## SMART on FHIR endpoints

```
authorization_endpoint  https://member.ibx.com/patientaccesssvc/oauth2/v1/authorize
token_endpoint          https://eapics.ibx.com/oauth2/v2/token
well-known              https://eapics.ibx.com/patient/v1/fhir/.well-known/smart-configuration
```

Advertised SMART capabilities: `client-public`, `sso-openid-connect`, `launch-standalone`, `client-confidential-symmetric`, `context-standalone-patient`, `permission-offline`, `permission-patient`.

## Repository layout

| Folder | Contents |
| --- | --- |
| `apis.yml` | APIs.json 0.19 index for IBX |
| `openapi/` | OpenAPI 3.0 specs split out of the published `cmsSwagger.json` (Patient / Provider / Formulary) |
| `capabilities/` | Naftiko capability YAMLs (Patient Access, Claims & EOB, Provider Directory, Medications & Formulary) |
| `rules/` | Spectral-style operational rules for the IBX FHIR APIs |
| `json-schema/` | JSON Schema for key FHIR resources (Patient, Coverage, EOB, Practitioner, Organization, Location) |
| `json-structure/` | JSON Structure describing IBX corporate / health-plan organization |
| `json-ld/` | JSON-LD context aligning IBX entities with schema.org and the FHIR IGs |
| `examples/` | Sample request/response payloads (Patient, Coverage, EOB, Practitioner, Organization, MedicationKnowledge) |
| `vocabulary/` | Operational vocabulary mapping IBX concepts, services, tools, standards |
| `plans/` | API Commons Plans 0.1 (the IBX FHIR APIs are free / regulatory-mandated) |
| `rate-limits/` | API Commons Rate Limits 0.1 (no public numeric limits; reasonable-use posture) |
| `finops/` | FOCUS-aligned FinOps file (no vendor invoice for API access) |

## Developer contacts

- Portal: <https://devportal.ibx.com/>
- Documentation (CMS Interoperability hub): <https://devportal.ibx.com/documentation/>
- Public Swagger / OpenAPI source: <https://www.ibx.com/scripts/custom/swagger/cmsSwagger.json>
- Registration: <https://devportal.ibx.com/cmssignin/>
- Terms & Conditions: <https://www.ibx.com/htdocs/custom/tnc/Developer%20Portal%20TandC.pdf>
- App onboarding support: <AppOnboardingSupport@ibx.com>

## Corporate structure

- **Parent**: Independence Health Group, Inc. (2013 holding company)
- **Sibling subsidiaries**: AmeriHealth (commercial), AmeriHealth Administrators (national TPA), AmeriHealth Insurance Company of New Jersey (commercial PPO/HMO, ~209,000 NJ members), AmeriHealth Caritas (Medicaid managed care; Independence Health Group 61.3% / Blue Cross Blue Shield of Michigan 38.7%), Tandigm Health (value-based primary care enablement)
- **Underwriting carrier brands** publishing Transparency in Coverage files: Keystone Health Plan East, QCC Insurance Company, Independence Assurance Co, Inc.

## Notable absences

- No public GitHub organization for IBX's developer surface — SDKs, sample code, and Postman collections are distributed through the dev portal rather than open-source repositories.
- No published numeric rate limits for any of the three FHIR APIs; consume them with exponential backoff and aggressive caching for the public Provider Directory / Formulary surfaces.
- The dev portal is a single-page Angular app (`devportal.ibx.com/documentation/`); deep links into per-API documentation pages are rendered client-side and are not directly fetchable by simple HTTP clients. The published `cmsSwagger.json` is the most reliable source of truth for paths, auth, and contact details.

## Standards alignment

HL7 FHIR R4 (4.0.1) · SMART App Launch 1.0.0 · US Core 3.1.1 · CARIN Blue Button · CPCDS · Da Vinci PDex · Da Vinci PDex Plan-Net · Da Vinci US Drug Formulary (USDF) · USCDI v1 · CMS Interoperability and Patient Access Final Rule (CMS-9115-F)
