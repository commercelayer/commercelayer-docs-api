---
description: The manual gateway object and its fields
---

# Manual gateways

Connect the manual payment gateway in order to be able to safely process payments through wire-transfer.

## The manual gateway object

A **manual gateway** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `manual_gateways` |
| **id** | `string` | The manual gateway unique identifier |
| links.**self** | `string` | The manual gateway endpoint URL |
| attributes.**name** | `string` | The payment gateway's internal name. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| attributes.**require\_capture** | `boolean` | Indicates if the gateway requires to captured. |
| relationships.**payment\_methods** | `array` | The associated payment methods. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

