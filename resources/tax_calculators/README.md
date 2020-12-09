---
description: The tax calculator object and its fields
---

# Tax calculators

By connecting a tax calculator to a market, all the market orders get automatic tax calculation.


### The tax calculator object

A **tax calculator** object is returned as part of the response body of each successful create, list, retrieve, or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `tax_calculators` |
| **id** | `string` | The tax calculator unique identifier |
| links.**self** | `string` | The tax calculator endpoint URL |
| attributes.**name** | `string` | The tax calculator's internal name. |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**tax_categories** | `array` | The associated tax categories. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

