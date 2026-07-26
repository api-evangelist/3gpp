---
name: Request quality of service on demand for an application session
description: Use the AS Session with QoS API (TS 29.122) to ask the mobile network for a QoS treatment for a specific application flow, then modify and release it.
api: openapi/3gpp-ts29122-assessionwithqos.yml
generated: '2026-07-25'
method: generated
operations:
  - CreateASSessionWithQoSSubscription
  - FetchAllASSessionWithQoSSubscriptions
  - FetchIndASSessionWithQoSSubscription
  - UpdateIndASSessionWithQoSSubscription
  - ModifyIndASSessionWithQoSSubscription
  - DeleteIndASSessionWithQoSSubscription
---

# Request QoS on demand (NEF, TS 29.122)

This is the 3GPP interface underneath every "network quality on demand" / "boosted connectivity" product. An
application function describes a flow between an application server and a device and asks the network for a
QoS reference; the network answers, and then notifies the AF when it can no longer honour it.

## Before you start

- Base URL `{apiRoot}/3gpp-as-session-with-qos/v1`, AF-scoped by `{scsAsId}`. `apiRoot` is operator supplied.
- QoS is requested by **reference** (`qosReference`), not by raw bitrates: the operator publishes the QoS
  profiles it supports and you name one. Do not invent values.
- A QoS request is a *write with real network consequence* — treat it as such in an agent context. See
  `agentic-access/3gpp-agentic-access.yml`.

## Steps

1. **Create the subscription.** `CreateASSessionWithQoSSubscription`
   (`POST {apiRoot}/3gpp-as-session-with-qos/v1/{scsAsId}/subscriptions`). Body identifies the UE
   (`ueIpv4Addr` / `ueIpv6Addr` / `externalId`), the flow descriptors, the `qosReference`, and
   `notificationDestination` for QoS notifications. Persist the `Location` returned on `201`.
2. **Listen for QoS notifications.** The specification declares a `notificationDestination` callback; the
   network POSTs there when the requested QoS is granted, degraded or lost. Handle the degraded case — it is
   the normal outcome under congestion, not an exception.
3. **Read back before you retry.** `FetchIndASSessionWithQoSSubscription`, or
   `FetchAllASSessionWithQoSSubscriptions` for the whole AF. There is no idempotency key: a timed-out create
   may have succeeded.
4. **Change the flow.** `UpdateIndASSessionWithQoSSubscription` (`PUT`, full replace) or
   `ModifyIndASSessionWithQoSSubscription` (`PATCH`, `application/merge-patch+json`) to change flow
   descriptors or the QoS reference mid-session.
5. **Always release.** `DeleteIndASSessionWithQoSSubscription` when the application session ends. Leaked QoS
   subscriptions consume operator resources and are usually chargeable.

## Failure handling

- `400` — the flow description or `qosReference` is not one the operator supports.
- `403` — the AF is not authorized for QoS on this subscriber or this DNN/S-NSSAI.
- `404` — subscription gone; do not PATCH, re-create.
- `429` / `503` — the exposure function is overloaded; back off per `Retry-After` and do not escalate the QoS
  request as a workaround.
