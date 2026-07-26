---
name: Subscribe to UE monitoring events through the NEF
description: Create, read, modify and delete monitoring event subscriptions on the 3GPP northbound exposure API (TS 29.122) and receive the notifications the network posts back.
api: openapi/3gpp-ts29122-monitoringevent.yml
generated: '2026-07-25'
method: generated
operations:
  - CreateMonitoringEventSubscription
  - FetchAllMonitoringEventSubscriptions
  - FetchIndMonitoringEventSubscription
  - UpdateIndMonitoringEventSubscription
  - ModifyIndMonitoringEventSubscription
  - DeleteIndMonitoringEventSubscription
---

# Subscribe to UE monitoring events (NEF / SCEF, TS 29.122)

Monitoring events are how an application function asks the mobile network to tell it about a device:
reachability, loss of connectivity, location reporting, roaming status, number of UEs in an area. This is the
subscribe-and-be-notified pattern that CAMARA device-status APIs are built on top of.

## Before you start

- Base URL is `{apiRoot}/3gpp-monitoring-event/v1` — `apiRoot` comes from the operator or from CAPIF discovery
  (see the CAPIF skill). 3GPP hosts nothing.
- You are identified as an AF by `{scsAsId}` in the path; subscriptions are collection-scoped to it.
- OAuth2 client credentials bearer token; RFC 7807 problem details on error.
- **You must expose a callback.** The `notificationDestination` you supply on create is the URI the network
  POSTs notifications to. It must be reachable from the operator network over HTTPS.

## Steps

1. **Create the subscription.** `CreateMonitoringEventSubscription`
   (`POST {apiRoot}/3gpp-monitoring-event/v1/{scsAsId}/subscriptions`). Body carries the target UE
   (`externalId`, `msisdn` or `externalGroupId`), the `monitoringType`, `maximumNumberOfReports` or
   `monitorExpireTime`, and `notificationDestination`. The `Location` header of the `201` is the individual
   subscription resource — persist it, it is your handle for everything else.
2. **Handle the callback.** The specification models delivery as an OpenAPI callback named
   `notificationDestination`. Notifications arrive as `POST` with a JSON body correlated by the subscription
   URI. See `asyncapi/3gpp-notifications-webhooks.yml`. Respond `204` quickly and process asynchronously.
3. **Read back.** `FetchIndMonitoringEventSubscription` for one subscription,
   `FetchAllMonitoringEventSubscriptions` for everything this AF has open. Use this after any ambiguous
   failure rather than re-POSTing — there is no idempotency key in 3GPP APIs.
4. **Change it.** `UpdateIndMonitoringEventSubscription` replaces the whole subscription (`PUT`);
   `ModifyIndMonitoringEventSubscription` applies a partial change (`PATCH`, `application/merge-patch+json`).
5. **Delete it.** `DeleteIndMonitoringEventSubscription`. Subscriptions also expire on their own when
   `maximumNumberOfReports` is reached or `monitorExpireTime` passes — do not assume a silent subscription is
   still live, read it back.

## Feature negotiation

Send `supportedFeatures` on create and honour the value echoed back. 3GPP negotiates optional behaviour with
this bitmask rather than by minting new API versions, so the same `/v1` path behaves differently against
different Releases.

## Failure handling

- `400` — invalid request parameters or malformed input; the `ProblemDetails.cause` names the offending field.
- `403` — the AF is not authorized to monitor that subscriber. This is a subscription/consent problem at the
  operator, not something to retry.
- `404` — the subscription URI no longer exists (expired or deleted).
- `429` / `503` — back off per `Retry-After`.
