---
description: The merchant object and its fields
---

# Merchants

A merchant is the fiscal representative that is selling in a specific market. Tax calculators use the merchant's address \(and the shipping address\) to determine the tax rate for an order.

## The merchant object

A **merchant** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `merchants` |
| **id** | `string` | The merchant unique identifier |
| links.**self** | `string` | The merchant endpoint URL |
| attributes.**name** | `string` | The merchant's internal name |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**address** | `object` | The associated address. |
| relationships.**attachments** | `array` | The associated attachments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

