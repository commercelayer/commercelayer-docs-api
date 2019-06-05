---
description: The complete list of supported events for each resource
---

# Real-time webhooks

Commerce Layer provides a [webhook](https://en.wikipedia.org/wiki/Webhook) mechanism to react to specific events in real-time. Each time a subscribed event occurs, we trigger a `POST` request to the endpoint that you specified. The request contains a JSON payload in the same format as the REST API. For each resource, you can also configure the related resources that should be included in the request body.

### Supported events

| Resource | Events |
| :--- | :--- |
| **Orders** | `create` `pending` `draft` `place` `approve` `cancel` `authorize` `pay` `void` `refund` `start_fulfilling` `fulfill` `destroy` |
| **Shipments** | `create` `upcoming` `cancel` `on_hold` `picking` `packing` `ready_to_ship` `ship` `destroy` |
| **Customers** | `create` `acquired` `repeat` `destroy` |
| **Customer subscriptions** | `create` `destroy` |
| **Customer password resets** | `create` `destroy` |

