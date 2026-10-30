# Independence Blue Cross

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

Independence Blue Cross (IBX) is the Blue Cross Blue Shield Association licensee for southeastern Pennsylvania (Bucks, Chester, Delaware, Montgomery, and Philadelphia counties) and a subsidiary of Independence Health Group, Inc., the parent holding company that consolidated IBX, AmeriHealth (commercial, including AmeriHealth New Jersey and the AmeriHealth Administrators TPA business), and the AmeriHealth Caritas family of Medicaid managed care plans in 2013. The company has called Philadelphia home for more than 85 years, serves nearly three million members directly, and — through Independence Health Group — supports roughly nine million covered lives across commercial, Medicare Advantage, Medicaid, CHIP, dental, vision, and behavioral health lines of business. Independence Health Group reported consolidated revenue of $36.3 billion for 2025. To satisfy the CMS Interoperability and Patient Access final rule (CMS-9115-F), IBX publishes three HL7 FHIR R4 (4.0.1) APIs from its `eapics.ibx.com` gateway and developer portal at `devportal.ibx.com`: a SMART-on-FHIR / OAuth 2.0 secured Patient Access API for Medicare Advantage and Keystone HMO CHIP members, a public Da Vinci PDex Plan-Net Provider Directory API, and a public Da Vinci US Drug Formulary (USDF) API. The provider also publishes monthly Transparency in Coverage machine-readable files (in-network rates, allowed amounts, prescription drugs) for three carrier brands — Keystone Health Plan East, QCC Insurance Company, and Independence Assurance Co, Inc.

**Areas:** Healthcare · Health Insurance · Blue Cross Blue Shield · Managed Care · Medicare · Medicare Advantage · Medicaid · CHIP · Commercial · Dental · Vision · Behavioral Health

## Independence Blue Cross on APIs.io

Everything profiled for Independence Blue Cross is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/independence-blue-cross/](https://apis.io/providers/independence-blue-cross/)** — or go straight to one of the APIs or properties below.

### APIs (4)

- [Independence Blue Cross Transparency In Coverage Data](https://apis.io/apis/independence-blue-cross/transparency-in-coverage/) — Monthly machine-readable JSON files published under 45 CFR Part Â§147.211 / the Transparency in Coverage rule for three carrier brands operated by…
- [Independence Blue Cross Formulary API](https://apis.io/apis/independence-blue-cross/independence-blue-cross-formulary-api/) — Public Da Vinci USDF FHIR R4 drug formulary resources.
- [Independence Blue Cross Patient Access API](https://apis.io/apis/independence-blue-cross/independence-blue-cross-patient-access-api/) — FHIR R4 Patient Access resources for member-authorized access.
- [Independence Blue Cross Provider Directory API](https://apis.io/apis/independence-blue-cross/independence-blue-cross-provider-directory-api/) — Public Da Vinci Plan-Net FHIR R4 provider directory resources.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [independence-blue-cross](https://apis.io/servers/independence-blue-cross/independence-blue-cross/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Independence Blue Cross Agentic Access](https://apis.io/agentic-access/independence-blue-cross/independence-blue-cross-agentic-access/)

#### JSON Schema (6)

The data models the API reads and writes.

- [IBX Coverage (CARIN BB subset)](https://apis.io/schemas/independence-blue-cross/independence-blue-cross-coverage/)
- [IBX ExplanationOfBenefit (CARIN BB subset)](https://apis.io/schemas/independence-blue-cross/independence-blue-cross-explanation-of-benefit/)
- [IBX Location (Da Vinci Plan-Net subset)](https://apis.io/schemas/independence-blue-cross/independence-blue-cross-location/)
- [IBX Organization (Da Vinci Plan-Net subset)](https://apis.io/schemas/independence-blue-cross/independence-blue-cross-organization/)
- [IBX Patient (US Core 3.1.1 subset)](https://apis.io/schemas/independence-blue-cross/independence-blue-cross-patient/)
- [IBX Practitioner (Da Vinci Plan-Net subset)](https://apis.io/schemas/independence-blue-cross/independence-blue-cross-practitioner/)

#### JSON Structure (1)

Data models expressed in JSON Structure.

- [Independence Blue Cross Health Plan Structure](https://apis.io/json-structure/independence-blue-cross/independence-blue-cross-health-plan-structure/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Independence Blue Cross Context](https://apis.io/jsonld/independence-blue-cross/independence-blue-cross-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Independence Blue Cross Vocabulary](https://apis.io/vocabularies/independence-blue-cross/independence-blue-cross-vocabulary/)

#### Examples (6)

Example requests and responses.

- [Independence Blue Cross Coverage Search Example](https://apis.io/examples/independence-blue-cross/independence-blue-cross-coverage-search-example/)
- [Independence Blue Cross Explanation Of Benefit Search Example](https://apis.io/examples/independence-blue-cross/independence-blue-cross-explanation-of-benefit-search-example/)
- [Independence Blue Cross Medication Knowledge Search Example](https://apis.io/examples/independence-blue-cross/independence-blue-cross-medication-knowledge-search-example/)
- [Independence Blue Cross Organization Search Example](https://apis.io/examples/independence-blue-cross/independence-blue-cross-organization-search-example/)
- [Independence Blue Cross Patient Read Example](https://apis.io/examples/independence-blue-cross/independence-blue-cross-patient-read-example/)
- [Independence Blue Cross Practitioner Search Example](https://apis.io/examples/independence-blue-cross/independence-blue-cross-practitioner-search-example/)

#### Collections (9)

Postman and Open Collection request collections.

- [Independence Blue Cross Drug Formulary FHIR API](https://apis.io/collections/independence-blue-cross/open-independence-blue-cross-formulary/)
- [Independence Blue Cross Drug FHIR Formulary API](https://apis.io/collections/independence-blue-cross/open-independence-blue-cross-formulary-api/)
- [Independence Blue Cross Patient Access FHIR API](https://apis.io/collections/independence-blue-cross/open-independence-blue-cross-patient/)
- [Independence Blue Cross Drug FHIR Formulary Patient Access API](https://apis.io/collections/independence-blue-cross/open-independence-blue-cross-patient-access-api/)
- [Independence Blue Cross Provider Directory FHIR API](https://apis.io/collections/independence-blue-cross/open-independence-blue-cross-provider/)
- [Independence Blue Cross Drug FHIR Formulary Provider Directory API](https://apis.io/collections/independence-blue-cross/open-independence-blue-cross-provider-directory-api/)
- [Independence Blue Cross Drug FHIR Formulary API](https://apis.io/collections/independence-blue-cross/postman-independence-blue-cross-formulary-api/)
- [Independence Blue Cross Drug FHIR Formulary Patient Access API](https://apis.io/collections/independence-blue-cross/postman-independence-blue-cross-patient-access-api/)
- [Independence Blue Cross Drug FHIR Formulary Provider Directory API](https://apis.io/collections/independence-blue-cross/postman-independence-blue-cross-provider-directory-api/)

#### Overlays (3)

OpenAPI overlays, including conversational phrasing for each operation.

- [Independence Blue Cross Formulary Api Overlay](https://apis.io/overlays/independence-blue-cross/independence-blue-cross-formulary-api-overlay/)
- [Independence Blue Cross Patient Access Api Overlay](https://apis.io/overlays/independence-blue-cross/independence-blue-cross-patient-access-api-overlay/)
- [Independence Blue Cross Provider Directory Api Overlay](https://apis.io/overlays/independence-blue-cross/independence-blue-cross-provider-directory-api-overlay/)

#### Governance rules (2)

Spectral rulesets for the provider's contracts.

- [Independence Blue Cross — jsonschema rules](https://apis.io/rules/independence-blue-cross/independence-blue-cross-jsonschema-spectral-rules/)
- [Independence Blue Cross API Rules](https://apis.io/rules/independence-blue-cross/independence-blue-cross-rules/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Independence Blue Cross Authentication](https://apis.io/security/independence-blue-cross/independence-blue-cross-authentication/)
- [Independence Blue Cross Domain Security](https://apis.io/security/independence-blue-cross/independence-blue-cross-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Independence Blue Cross Scopes](https://apis.io/scopes/independence-blue-cross/independence-blue-cross-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Independence Blue Cross Plans Pricing](https://apis.io/plans/independence-blue-cross/independence-blue-cross-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Independence Blue Cross Rate Limits](https://apis.io/rate-limits/independence-blue-cross/independence-blue-cross-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Independence Blue Cross Finops](https://apis.io/finops/independence-blue-cross/independence-blue-cross-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.ibx.com)
- [Documentation](https://devportal.ibx.com/documentation/)
- [Getting started](https://www.ibx.com/developer-resources/index.html)
- [Support](https://www.ibx.com/contact-us/index.html)
- [Blog](https://news.ibx.com/feed/)
- [Compliance](https://www.ibx.com/privacy-policy/hipaa-compliance.html)
- [Terms of service](https://www.ibx.com/htdocs/custom/tnc/Developer%20Portal%20TandC.pdf)
- [Privacy policy](https://www.ibx.com/privacy-policy)

## API Evangelist rating

**Kin Score 54.0** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 78.6 |
| Contract quality | 58.8 |
| Contract governance | 31.8 |
| Operational transparency | 15.8 |
| Developer ergonomics | 57.7 |
| Access clarity | 43.4 |

**Agent readiness 35.9** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | na |
| MCP Server | — |
| Auth Clarity | negotiable (partial credit) |
| Idempotency | na |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | derived (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | na |
| Delegated Identity | documented (partial credit) |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 47.7** — Health

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/independence-blue-cross/](https://apis.io/providers/independence-blue-cross/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Independence Blue Cross: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/independence-blue-cross/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
