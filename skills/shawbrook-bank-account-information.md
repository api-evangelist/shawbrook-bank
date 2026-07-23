---
name: Retrieve account information with OBIE AIS
description: Set up an account-access consent and read a customer's accounts, balances and transactions via the OBIE Account & Transaction (AIS) API that Shawbrook conforms to as an FCA-authorised ASPSP.
api: openapi/obie-account-info-openapi.yaml
standard: OBIE Account and Transaction API v4.0.1 (FAPI, unverified as a Shawbrook-hosted contract)
operations: [CreateAccountAccessConsents, GetAccountAccessConsentsConsentId, GetAccounts, GetAccountsAccountId, GetAccountsAccountIdBalances, GetAccountsAccountIdTransactions]
---

# Retrieve account information (OBIE AIS)

Use this to read a Payment Service User's (PSU) accounts under UK Open Banking. This is the shared OBIE standard an FCA-authorised ASPSP conforms to — a live Shawbrook ASPSP host and TPP onboarding (OBIE/eIDAS certificates) are required and are NOT provided here.

## Prerequisites
- Registered TPP with an AISP role and valid OBIE/eIDAS transport (mTLS) + signing certificates.
- Client-credentials access token (scope `accounts`) for TPP-context calls.
- FAPI headers on every request: `x-fapi-auth-date`, `x-fapi-customer-ip-address`, `x-fapi-interaction-id`, plus `Authorization`.

## Steps
1. **Create the consent** — `CreateAccountAccessConsents` (POST `/account-access-consents`) with the requested `Permissions` and expiry. Returns a `ConsentId` in status `AwaitingAuthorisation`.
2. **PSU authorisation** — redirect the PSU through the ASPSP authorization-code + SCA flow (`PSUOAuth2Security`) to authorise the `ConsentId`; exchange for a PSU-context access token.
3. **Confirm consent status** — `GetAccountAccessConsentsConsentId` and check status is `Authorised`.
4. **List accounts** — `GetAccounts` to enumerate the accounts the consent authorises.
5. **Read detail** — `GetAccountsAccountId`, then `GetAccountsAccountIdBalances` and `GetAccountsAccountIdTransactions` for each `AccountId`.

## Rules
- Paginate collections with the `page` param; follow `Links.Next` until absent (see conventions/shawbrook-bank-conventions.yml).
- Echo/track `x-fapi-interaction-id` for support correlation.
- Handle errors as the `OBErrorResponse1` envelope with `UK.OBIE.*` codes (see errors/shawbrook-bank-problem-types.yml); 403 means the consent/scope does not authorise the resource.
