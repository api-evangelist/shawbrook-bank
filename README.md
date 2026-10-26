# Shawbrook Bank (shawbrook-bank)

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

Shawbrook Bank Limited is a specialist UK savings and lending bank (part of Shawbrook Group plc, which listed on the London Stock Exchange in October 2025 after being owned by a consortium led by BC Partners and Pollen Street Capital). It is authorised by the PRA and regulated by the FCA and PRA, with deposits protected by the FSCS. Shawbrook focuses on personal and business savings and specialist lending — property finance, SME and asset finance, and consumer lending — rather than personal current accounts, so it is not one of the CMA-mandated banks (CMA9).

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/shawbrook-bank/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/shawbrook-bank/refs/heads/main/apis.yml)

## Open Banking Posture

Shawbrook operates within the UK Open Banking / PSD2 framework as an FCA-authorised deposit-taker, but it is primarily a **consumer** of Open Banking (it uses account verification via Consents.Online to confirm customers' linked nominated accounts) rather than a publisher of ASPSP surfaces. As of this review:

- **No public developer portal** — probes of `developer.shawbrook.co.uk` and `api.shawbrook.co.uk` did not resolve.
- **No confirmed Open Data endpoint** — probes of `shawbrook.co.uk/open-banking/...` paths and `/.well-known/open-banking` returned HTTP 404. As an online specialist bank with no branch/ATM network, its Open Data obligations are minimal.
- **No bank-specific Read/Write API host or spec** could be confirmed.

The OBIE Open Data and Read/Write API families below are represented as the **shared UK Open Banking standard** an FCA-authorised ASPSP conforms to — the specs harvested into `openapi/` are the OBIE standard documents, **not** verified Shawbrook contracts.

## Tags

- Financial Services
- Banking
- Savings
- Specialist Lending
- Open Banking
- PSD2
- OBIE
- United Kingdom
- Payments
- Account Information

## Timestamps

- **Created:** 2026-07-23
- **Modified:** 2026-07-23

## APIs

### Shawbrook Open Data API (OBIE Standard, Unverified)

UK Open Banking Open Data API — the public, unauthenticated reference-data surface (ATMs, branches, current accounts, SME loans, commercial credit cards) defined by the OBIE Open Data Standard v1.3. No Shawbrook-hosted endpoint could be confirmed.

- **Human URL:** [https://openbankinguk.github.io/opendata-api-docs-pub/v2.4.0/](https://openbankinguk.github.io/opendata-api-docs-pub/v2.4.0/)

#### Properties

- [OpenAPI](openapi/obie-opendata-swagger.json) — OBIE Open Data Standard v1.3 (Swagger 2.0), shared standard
- [Documentation](https://openbankinguk.github.io/opendata-api-docs-pub/v2.4.0/)
- [Source Code](https://github.com/OpenBankingUK/opendata-api-spec-compiled)

### Shawbrook Account & Transaction Information API (AIS, OBIE Standard, Unverified)

UK Open Banking Read/Write AISP surface per OBIE Account and Transaction API Specification v4.0.1 (OpenAPI 3.0.0). FAPI-secured — OAuth2/OIDC, mutual-TLS, PSD2 SCA — with OBIE/eIDAS-certificate onboarding.

- **Human URL:** [https://standards.openbanking.org.uk/api-specifications/](https://standards.openbanking.org.uk/api-specifications/)

#### Properties

- [OpenAPI](openapi/obie-account-info-openapi.yaml) — OBIE standard, shared (not a Shawbrook contract)
- [Documentation](https://standards.openbanking.org.uk/api-specifications/)
- [Source Code](https://github.com/OpenBankingUK/read-write-api-specs)

### Shawbrook Payment Initiation API (PIS, OBIE Standard, Unverified)

UK Open Banking Read/Write PISP surface per OBIE Payment Initiation API Specification v4.0.1 (OpenAPI 3.0.0). FAPI-secured with OAuth2/OIDC, mutual-TLS, and PSD2 SCA.

- **Human URL:** [https://standards.openbanking.org.uk/api-specifications/](https://standards.openbanking.org.uk/api-specifications/)

#### Properties

- [OpenAPI](openapi/obie-payment-initiation-openapi.yaml) — OBIE standard, shared
- [Documentation](https://standards.openbanking.org.uk/api-specifications/)
- [Source Code](https://github.com/OpenBankingUK/read-write-api-specs)

### Shawbrook Confirmation of Funds API (CBPII, OBIE Standard, Unverified)

UK Open Banking Read/Write CBPII surface per OBIE Confirmation of Funds API Specification v4.0.1 (OpenAPI 3.0.0). FAPI-secured with OAuth2/OIDC, mutual-TLS, and PSD2 SCA.

- **Human URL:** [https://standards.openbanking.org.uk/api-specifications/](https://standards.openbanking.org.uk/api-specifications/)

#### Properties

- [OpenAPI](openapi/obie-confirmation-funds-openapi.yaml) — OBIE standard, shared
- [Documentation](https://standards.openbanking.org.uk/api-specifications/)
- [Source Code](https://github.com/OpenBankingUK/read-write-api-specs)

## Common Properties

- [Website](https://www.shawbrook.co.uk/)
- [About](https://www.shawbrook.co.uk/about-us/)
- [Blog](https://www.shawbrook.co.uk/newsroom/)
- [Support](https://www.shawbrook.co.uk/help/)
- [Contact](https://www.shawbrook.co.uk/contact-us/)
- [Privacy Policy](https://www.shawbrook.co.uk/privacy-policy/)
- [LinkedIn](https://www.linkedin.com/company/shawbrook-bank/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
