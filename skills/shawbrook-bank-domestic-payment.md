---
name: Initiate a domestic payment with OBIE PIS
description: Create a domestic-payment consent, confirm funds, and initiate an idempotent domestic payment via the OBIE Payment Initiation (PIS) API Shawbrook conforms to as an FCA-authorised ASPSP.
api: openapi/obie-payment-initiation-openapi.yaml
standard: OBIE Payment Initiation API v4.0.1 (FAPI, unverified as a Shawbrook-hosted contract)
operations: [CreateDomesticPaymentConsents, GetDomesticPaymentConsentsConsentId, GetDomesticPaymentConsentsConsentIdFundsConfirmation, CreateDomesticPayments, GetDomesticPaymentsDomesticPaymentId]
---

# Initiate a domestic payment (OBIE PIS)

Use this to initiate a single domestic payment under UK Open Banking. Shared OBIE standard; requires a registered PISP and a live ASPSP host (not provided here).

## Prerequisites
- Registered TPP with a PISP role + OBIE/eIDAS mTLS and signing certificates.
- Client-credentials token (scope `payments`).
- Every write request carries `x-idempotency-key` (<=40 chars) and a detached `x-jws-signature`, plus the FAPI headers.

## Steps
1. **Create the payment consent** — `CreateDomesticPaymentConsents` (POST `/domestic-payment-consents`) with `Initiation` (amount, creditor account, reference). Returns `ConsentId`.
2. **PSU authorisation + SCA** — redirect the PSU through `PSUOAuth2Security` to authorise the `ConsentId`; obtain the PSU-context token.
3. **Check status / funds** — `GetDomesticPaymentConsentsConsentId` (expect `Authorised`), optionally `GetDomesticPaymentConsentsConsentIdFundsConfirmation` to confirm sufficient funds.
4. **Initiate the payment** — `CreateDomesticPayments` (POST `/domestic-payments`) referencing the `ConsentId`, with a fresh `x-idempotency-key`. The `Initiation` block must be identical to the consent.
5. **Track settlement** — `GetDomesticPaymentsDomesticPaymentId` to poll payment status.

## Rules
- **Idempotency:** replaying step 4 with the same `x-idempotency-key` returns the original payment, never a duplicate (see conventions/shawbrook-bank-conventions.yml).
- The `Initiation` in the payment must byte-match the consent, or the ASPSP rejects with a `UK.OBIE.*` error.
- Errors use the `OBErrorResponse1` envelope (errors/shawbrook-bank-problem-types.yml); `UK.OBIE.Signature.Invalid` means the JWS failed verification.
