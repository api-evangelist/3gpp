---
name: Deliver non-IP data and trigger IoT devices through the NEF
description: Configure non-IP data delivery (NIDD) for a device, send downlink data, and trigger a device over the control plane using the 3GPP northbound exposure APIs (TS 29.122).
api: openapi/3gpp-ts29122-nidd.yml
generated: '2026-07-25'
method: generated
operations:
  - CreateNIDDConfiguration
  - FetchAllNIDDConfigurations
  - FetchIndNIDDConfiguration
  - ModifyNIDDConfiguration
  - DeleteNIDDConfiguration
  - CreateDownlinkDataDelivery
  - FetchAllDownlinkDataDeliveries
  - FetchIndDownlinkDataDelivery
  - UpdateIndDownlinkDataDelivery
  - DeleteIndDownlinkDataDelivery
  - CreateDeviceTriggeringTransaction
---

# Non-IP data delivery and device triggering (NEF, TS 29.122)

Cellular IoT devices often have no IP session. 3GPP exposes two control-plane paths for reaching them: NIDD,
which carries small data payloads through the core network, and device triggering, which wakes a device so it
opens its own connection. Both are AF-scoped northbound APIs.

## Before you start

- NIDD base URL `{apiRoot}/3gpp-nidd/v1`, device triggering `{apiRoot}/3gpp-device-triggering/v1`. `apiRoot`
  is operator supplied; discover it through CAPIF.
- Payloads are small and the network may buffer, reorder or drop them. Delivery is reported asynchronously via
  the callback you register — a `201` means accepted, not delivered.
- These are physically consequential operations: they move bytes to, and wake, real devices. Rate-limit them
  in any agent context and log every invocation.

## Steps

1. **Configure NIDD for the device.** `CreateNIDDConfiguration`
   (`POST {apiRoot}/3gpp-nidd/v1/{scsAsId}/configurations`) with the device identity, the reliable-data-service
   parameters and `notificationDestination`. Persist the `Location`.
2. **Send downlink data.** `CreateDownlinkDataDelivery`
   (`POST .../configurations/{configurationId}/downlink-data-deliveries`). Track the returned resource with
   `FetchIndDownlinkDataDelivery`; use `UpdateIndDownlinkDataDelivery` to replace a pending delivery and
   `DeleteIndDownlinkDataDelivery` to cancel one that has not yet been delivered.
3. **Receive uplink and delivery status.** The `niddNotifications` callback delivers uplink data and delivery
   outcomes to the URI you registered. See `asyncapi/3gpp-notifications-webhooks.yml`.
4. **Trigger a sleeping device.** `CreateDeviceTriggeringTransaction`
   (`POST {apiRoot}/3gpp-device-triggering/v1/{scsAsId}/transactions`) with the trigger payload, validity
   period and priority. The result of the trigger arrives on the transaction's `notificationDestination`
   callback, not in the response body.
5. **Audit and clean up.** `FetchAllNIDDConfigurations` and `FetchAllDownlinkDataDeliveries` list what is
   open; `ModifyNIDDConfiguration` (`PATCH`) adjusts a configuration; `DeleteNIDDConfiguration` removes it.

## Failure handling

- `400` — payload exceeds the negotiated maximum size, or the configuration parameters are invalid.
- `403` — the AF is not authorized for NIDD or triggering on this subscriber.
- `404` — configuration or transaction not found; re-read before re-sending, there is no idempotency key and
  a retry can double-deliver.
- `409` — a configuration already exists for that device; fetch it rather than creating a second one.
- `429` / `503` — back off; do not retry device triggers in a tight loop, they cost radio resources.
