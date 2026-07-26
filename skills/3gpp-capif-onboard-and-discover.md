---
name: Onboard an API invoker and discover northbound service APIs with CAPIF
description: Use the 3GPP Common API Framework (TS 29.222) to onboard an invoker, establish a security context, obtain an access token and discover the service APIs an operator has published.
api: openapi/3gpp-ts29222-capif-api-invoker-management-api.yml
generated: '2026-07-25'
method: generated
operations:
  - CreateOnboardedAPIInvoker
  - UpdateIndOnboardedAPIInvoker
  - DeleteIndOnboardedAPIInvoker
  - CreateSecIndTrustedAPIInv
  - GetSecIndTrustedAPIInv
  - GetOAuthIndAPIInv
  - GetPubServAPIs
---

# Onboard an API invoker and discover service APIs (CAPIF)

CAPIF is 3GPP's own API management standard. Before an application can call any northbound API an operator
exposes, it has to be onboarded as an *API invoker*, given a security context, and issued a token. This skill
is the sequence for doing that. Every operation below exists verbatim in the specifications in `openapi/`.

## Before you start

- **There is no 3GPP endpoint.** Every server entry is `{apiRoot}/<api-name>/v1`. The operator or exposure
  platform gives you `apiRoot` and the `{tokenUrl}`. If you do not have those, you cannot run this skill.
- Transport is HTTP/2 over TLS with `application/json` bodies (TS 29.500).
- Auth is OAuth2 **client credentials**. See `authentication/3gpp-authentication.yml`.
- Errors are RFC 7807 problem details (`application/problem+json`, `ProblemDetails`). See
  `errors/3gpp-problem-types.yml`.
- **There is no idempotency key.** Do not blind-retry a `POST` — re-read the resource first. See
  `conventions/3gpp-conventions.yml`.

## Steps

1. **Onboard the invoker.** `CreateOnboardedAPIInvoker`
   (`openapi/3gpp-ts29222-capif-api-invoker-management-api.yml`, `POST {apiRoot}/api-invoker-management/v1/onboardedInvokers`).
   Send the invoker's enrolment details and public key. The response carries the assigned `apiInvokerId` and the
   `Location` of the individual invoker resource. Keep both; every later call is scoped by `apiInvokerId`.
2. **Create the security context.** `CreateSecIndTrustedAPIInv`
   (`openapi/3gpp-ts29222-capif-security-api.yml`, `PUT {apiRoot}/capif-security/v1/trustedInvokers/{apiInvokerId}`).
   Declare the security methods you support for each service API you intend to call.
3. **Request an access token.** `GetOAuthIndAPIInv`
   (`openapi/3gpp-ts29222-capif-security-api.yml`). This is the CAPIF client-credentials token grant; the scope
   values are per service API — see `scopes/3gpp-scopes.yml` for the scope strings the specifications declare.
4. **Discover what you are allowed to call.** `GetPubServAPIs`
   (`openapi/3gpp-ts29222-capif-discover-service-api.yml`,
   `GET {apiRoot}/service-apis/v1/allServiceAPIs?api-invoker-id=...`). The response is the filtered catalog of
   service APIs published to this CAPIF core function for this invoker, including each API's version and
   interface descriptions. Use the returned interface descriptions to build the base URL for the actual
   northbound call — do not hardcode one.
5. **Verify the context when a call is rejected.** `GetSecIndTrustedAPIInv` returns the current authentication
   and authorization information for the invoker; use it to distinguish "token expired" from "not authorized
   for this service API" before retrying.
6. **Keep the registration current, and clean up.** `UpdateIndOnboardedAPIInvoker` to replace the invoker
   details, `DeleteIndOnboardedAPIInvoker` to offboard.

## Failure handling

- `401` — token missing, expired or issued for a different service API. Re-run step 3.
- `403` — the invoker is onboarded but not authorized for that service API. Re-run step 2, then step 4.
- `404` — the `apiInvokerId` is unknown to this CAPIF core function; you are talking to the wrong deployment.
- `429` / `503` — producer overload. Respect `Retry-After`; TS 29.500 defines overload control behaviour.
