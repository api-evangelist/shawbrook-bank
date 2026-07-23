# Shawbrook Bank (shawbrook-bank)

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
