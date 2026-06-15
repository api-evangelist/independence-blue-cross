# Independence Blue Cross (independence-blue-cross)

Independence Blue Cross (IBX) is the Blue Cross Blue Shield Association licensee for southeastern Pennsylvania (Bucks, Chester, Delaware, Montgomery, and Philadelphia counties) and a subsidiary of Independence Health Group, Inc., the parent holding company that consolidated IBX, AmeriHealth (commercial, including AmeriHealth New Jersey and the AmeriHealth Administrators TPA business), and the AmeriHealth Caritas family of Medicaid managed care plans in 2013. The company has called Philadelphia home for more than 85 years, serves nearly three million members directly, and — through Independence Health Group — supports roughly nine million covered lives across commercial, Medicare Advantage, Medicaid, CHIP, dental, vision, and behavioral health lines of business. Independence Health Group reported consolidated revenue of $36.3 billion for 2025. To satisfy the CMS Interoperability and Patient Access final rule (CMS-9115-F), IBX publishes three HL7 FHIR R4 (4.0.1) APIs from its `eapics.ibx.com` gateway and developer portal at `devportal.ibx.com`: a SMART-on-FHIR / OAuth 2.0 secured Patient Access API for Medicare Advantage and Keystone HMO CHIP members, a public Da Vinci PDex Plan-Net Provider Directory API, and a public Da Vinci US Drug Formulary (USDF) API. The provider also publishes monthly Transparency in Coverage machine-readable files (in-network rates, allowed amounts, prescription drugs) for three carrier brands — Keystone Health Plan East, QCC Insurance Company, and Independence Assurance Co, Inc.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/independence-blue-cross/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/independence-blue-cross/refs/heads/main/apis.yml)

## Scope

- **Type:** Index

## Tags

- Healthcare
- Health Insurance
- Blue Cross Blue Shield
- Managed Care
- Medicare
- Medicare Advantage
- Medicaid
- CHIP
- Commercial
- Dental
- Vision
- Behavioral Health
- Pharmacy Benefits
- Interoperability
- FHIR
- SMART On FHIR
- CMS
- Patient Access
- Provider Directory
- Drug Formulary
- Transparency In Coverage

## Timestamps

- **Created:** 2024-01-01
- **Modified:** 2026-05-23

## APIs

### Independence Blue Cross Patient Access FHIR API

HL7 FHIR R4 (4.0.1) Patient Access API published to satisfy the CMS Interoperability and Patient Access final rule (CMS-9115-F). Enables Independence Medicare Advantage and Keystone HMO CHIP members (or their personal representatives) to consent and share clinical, claims, encounter, coverage, medication, immunization, and demographic data with registered third-party applications. Conforms to the CARIN for Blue Button (CARIN BB), Common Payer Consumer Data Set (CPCDS), US Core 3.1.1, and Da Vinci PDex profiles. Secured by SMART App Launch 1.0.0 over OAuth 2.0 / OpenID Connect; production access requires developer registration and CMS-aligned attestation.

- **Human URL:** [https://devportal.ibx.com/documentation/](https://devportal.ibx.com/documentation/)
- **Base URL:** `https://eapics.ibx.com/patient/v1/fhir`

#### Tags

- Patient Access
- FHIR
- SMART On FHIR
- Medicare Advantage
- CHIP
- CMS

#### Properties

- [Portal](https://devportal.ibx.com/)
- [Documentation](https://devportal.ibx.com/documentation/)
- [Swagger](https://www.ibx.com/scripts/custom/swagger/cmsSwagger.json)
- [Capability Statement](https://eapics.ibx.com/patient/v1/fhir/metadata)
- [Smart Configuration](https://eapics.ibx.com/patient/v1/fhir/.well-known/smart-configuration)
- [Authorize U R L](https://member.ibx.com/patientaccesssvc/oauth2/v1/authorize)
- [Token U R L](https://eapics.ibx.com/oauth2/v2/token)
- [Registration](https://devportal.ibx.com/cmssignin/)
- [Terms of Service](https://www.ibx.com/htdocs/custom/tnc/Developer%20Portal%20TandC.pdf)
- [Contact Email](mailto:AppOnboardingSupport@ibx.com)
- [OpenAPI](openapi/independence-blue-cross-patient-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/independence-blue-cross-patient.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/independence-blue-cross-patient.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Spectral Rules](rules/independence-blue-cross-rules.yml)
- [JSON Schema](json-schema/independence-blue-cross-patient-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/independence-blue-cross-coverage-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/independence-blue-cross-explanation-of-benefit-schema.json) — [JSON Schema](https://json-schema.org/specification)

### Independence Blue Cross Provider Directory FHIR API

HL7 FHIR R4 (4.0.1) Provider Directory API satisfying the CMS Provider Directory requirement of the Interoperability and Patient Access final rule. Published as a Da Vinci PDex Plan-Net server (CapabilityStatement id `ibc-plan-net-metadata`, published 2021-05-28). Publishes Practitioner, PractitionerRole, Organization, OrganizationAffiliation, Location, HealthcareService, InsurancePlan, and Endpoint resources for the Independence Blue Cross provider and pharmacy network. Publicly queryable; no authentication or member consent required.

- **Human URL:** [https://devportal.ibx.com/documentation/](https://devportal.ibx.com/documentation/)
- **Base URL:** `https://eapics.ibx.com/provider/v1/fhir`

#### Tags

- Provider Directory
- FHIR
- Da Vinci
- Plan-Net
- CMS

#### Properties

- [Portal](https://devportal.ibx.com/)
- [Documentation](https://devportal.ibx.com/documentation/)
- [Swagger](https://www.ibx.com/scripts/custom/swagger/cmsSwagger.json)
- [Capability Statement](https://eapics.ibx.com/provider/v1/fhir/metadata)
- [Implementation Guide](http://hl7.org/fhir/us/davinci-pdex-plan-net/ImplementationGuide/hl7.fhir.us.davinci-pdex-plan-net)
- [OpenAPI](openapi/independence-blue-cross-provider-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/independence-blue-cross-provider.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/independence-blue-cross-provider.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Spectral Rules](rules/independence-blue-cross-rules.yml)
- [JSON Schema](json-schema/independence-blue-cross-practitioner-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/independence-blue-cross-organization-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/independence-blue-cross-location-schema.json) — [JSON Schema](https://json-schema.org/specification)

### Independence Blue Cross Drug Formulary FHIR API

HL7 FHIR R4 (4.0.1) Drug Formulary API satisfying the CMS Interoperability drug formulary publication requirement, published as a Da Vinci US Drug Formulary (USDF) server (CapabilityStatement id `usdf-server`, published 2021-06-03). Exposes covered drug lists, tiers, and prior authorization indicators via FHIR `List` and `MedicationKnowledge` resources. Publicly queryable; no authentication required.

- **Human URL:** [https://devportal.ibx.com/documentation/](https://devportal.ibx.com/documentation/)
- **Base URL:** `https://eapics.ibx.com/formulary/v1/fhir`

#### Tags

- Formulary
- Drug Formulary
- FHIR
- Da Vinci
- USDF
- CMS
- Pharmacy Benefits

#### Properties

- [Portal](https://devportal.ibx.com/)
- [Documentation](https://devportal.ibx.com/documentation/)
- [Swagger](https://www.ibx.com/scripts/custom/swagger/cmsSwagger.json)
- [Capability Statement](https://eapics.ibx.com/formulary/v1/fhir/metadata)
- [Implementation Guide](http://hl7.org/fhir/us/davinci-drug-formulary/ImplementationGuide/hl7.fhir.us.davinci-drug-formulary)
- [OpenAPI](openapi/independence-blue-cross-formulary-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/independence-blue-cross-formulary.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/independence-blue-cross-formulary.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Spectral Rules](rules/independence-blue-cross-rules.yml)

### Independence Blue Cross Transparency In Coverage Data

Monthly machine-readable JSON files published under 45 CFR Part Â§147.211 / the Transparency in Coverage rule for three carrier brands operated by Independence Blue Cross: Keystone Health Plan East, QCC Insurance Company, and Independence Assurance Co, Inc. Files cover in-network negotiated rates, out-of-network allowed amounts, and prescription drug pricing across medical, dental, vision, pharmacy, and plan domains.

- **Human URL:** [https://www.ibx.com/resources/for-members/transparency-in-coverage.html](https://www.ibx.com/resources/for-members/transparency-in-coverage.html)
- **Base URL:** `https://www.ibx.com/cmstic/`

#### Tags

- Transparency In Coverage
- Machine Readable Files
- Pricing
- Regulatory

#### Properties

- [Index](https://www.ibx.com/cmstic/?brand=khpe)
- [Index](https://www.ibx.com/cmstic/?brand=qcc)
- [Index](https://www.ibx.com/cmstic/?brand=iac)
- [Regulation](https://www.cms.gov/healthplan-price-transparency)
- [Postman Collection](collections/independence-blue-cross-formulary.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/independence-blue-cross-formulary.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/independence-blue-cross-patient.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/independence-blue-cross-patient.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/independence-blue-cross-provider.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/independence-blue-cross-provider.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Independence Blue Cross Corporate Website

Public corporate website for Independence Blue Cross hosting member, provider, employer, broker, and producer portals; product pages for Medicare Advantage, commercial, dental, and vision; the affiliates / Independence Health Group corporate page; and pointers to the CMS Interoperability developer portal at devportal.ibx.com.

- **Human URL:** [https://www.ibx.com](https://www.ibx.com)
- **Base URL:** `https://www.ibx.com`

#### Tags

- Website
- Corporate

#### Properties

- [Website](https://www.ibx.com)
- [About Us](https://www.ibx.com/about-us)
- [Affiliates](https://www.ibx.com/about-us/affiliates)
- [Annual Reports](https://www.ibx.com/about-us/annual-reports)
- [Newsroom](https://news.ibx.com/)
- [Developer Portal](https://devportal.ibx.com/)
- [Provider Resources](https://www.ibx.com/resources/for-providers/index.html)
- [Postman Collection](collections/independence-blue-cross-formulary.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/independence-blue-cross-formulary.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/independence-blue-cross-patient.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/independence-blue-cross-patient.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/independence-blue-cross-provider.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/independence-blue-cross-provider.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Portal](https://devportal.ibx.com/)
- [Website](https://www.ibx.com)
- [Documentation](https://devportal.ibx.com/documentation/)
- [Swagger](https://www.ibx.com/scripts/custom/swagger/cmsSwagger.json)
- [Authentication](https://eapics.ibx.com/patient/v1/fhir/.well-known/smart-configuration)
- [Registration](https://devportal.ibx.com/cmssignin/)
- [Terms of Service](https://www.ibx.com/htdocs/custom/tnc/Developer%20Portal%20TandC.pdf)
- [Privacy Policy](https://www.ibx.com/privacy-policy)
- [Login](https://www.ibx.com/login)
- [C M S Final Rule](https://www.cms.gov/priorities/key-initiatives/burden-reduction/interoperability)
- [C A R I N Blue Button](https://hl7.org/fhir/us/carin-bb/history.html)
- [Da Vinci P Dex](https://hl7.org/fhir/us/davinci-pdex/history.html)
- [Da Vinci Plan Net](http://hl7.org/fhir/us/davinci-pdex-plan-net/ImplementationGuide/hl7.fhir.us.davinci-pdex-plan-net)
- [Da Vinci U S D F](http://hl7.org/fhir/us/davinci-drug-formulary/ImplementationGuide/hl7.fhir.us.davinci-drug-formulary)
- [U S Core](https://hl7.org/fhir/us/core/STU3.1.1/)
- [S M A R T App Launch](https://hl7.org/fhir/smart-app-launch/1.0.0/)
- [Affiliates](https://www.ibx.com/about-us/affiliates)
- [Contact Us](mailto:AppOnboardingSupport@ibx.com)
- [Contact Support](https://www.ibx.com/contact-us)
- [News Blog](https://news.ibx.com/)
- [Transparency In Coverage](https://www.ibx.com/resources/for-members/transparency-in-coverage.html)
- [Facebook](https://www.facebook.com/ibx)
- [Twitter](https://www.twitter.com/ibx)
- [YouTube](https://www.youtube.com/ibxphilly)
- [Instagram](https://www.instagram.com/ibxfearless/)
- [Pinterest](https://pinterest.com/IBXBlueCross/)
- [Anti Fraud](https://www.ibx.com/anti-fraud)
- [Plans](plans/independence-blue-cross-plans-pricing.yml)
- [Rate Limits](rate-limits/independence-blue-cross-rate-limits.yml)
- [Fin Ops](finops/independence-blue-cross-finops.yml)
- [Vocabulary](vocabulary/independence-blue-cross-vocabulary.yml)
- [J S O N L D Context](json-ld/independence-blue-cross-context.jsonld)
- [JSON Structure](json-structure/independence-blue-cross-health-plan-structure.json)
- [Features](undefined)
- [Use Cases](undefined)
- [Integrations](undefined)
- [Solutions](undefined)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
