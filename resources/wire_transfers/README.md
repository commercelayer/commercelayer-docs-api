---
description: The wire transfer object and its fields
---

# Wire transfers

Wire transfers can be associated with orders as their payment sources. Being manual payments, they are always authorized.

## The wire transfer object

A **wire transfer** object is returned as part of the response body of each successful [create](https://docs.commercelayer.io/api/resources/wire_transfers/create_wire_transfer), [list](https://docs.commercelayer.io/api/resources/wire_transfers/list_wire_transfers), [retrieve](https://docs.commercelayer.io/api/resources/wire_transfers/retrieve_wire_transfer), or [update](https://docs.commercelayer.io/api/resources/wire_transfers/update_wire_transfer) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `wire_transfers` |
| **id** | `string` | The wire transfer unique identifier |
| links.**self** | `string` | The wire transfer endpoint URL |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**order** | `object` | The order associated to the wiretransfer payment, that is set as its payment source. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

