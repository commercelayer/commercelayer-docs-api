---
description: The external tax calculator object and its fields
---

# External tax calculators

Create an external tax calculator to delegate tax calculation logic to the specified external service. Use the order payload to compute your own logic and return the tax rate to be applied to the order.

## The external tax calculator object

An **external tax calculator** object is returned as part of the response body of each successful create, list, retrieve, or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `external_tax_calculators` |
| **id** | `string` | The external tax calculator unique identifier |
| links.**self** | `string` | The external tax calculator endpoint URL |
| attributes.**name** | `string` | The tax calculator's internal name. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| attributes.**tax\_calculator\_url** | `string` | The URL to the service that will compute the taxes. |
| relationships.**tax\_categories** | `array` | The associated tax categories. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

