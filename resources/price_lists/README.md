---
description: The price list object and its fields
---

# Price lists

Price lists determine the SKU prices and their currency within a market. Create more price lists if you need to manage international business models or B2B/B2C.


### The price list object

A **price list** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `price_lists` |
| **id** | `string` | The price list unique identifier |
| links.**self** | `string` | The price list endpoint URL |
| attributes.**name** | `string` | The market's internal name |
| attributes.**currency_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard. |
| attributes.**tax_included** | `boolean` | Indicates if the associated prices include taxes. |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**prices** | `array` | The associated prices. |
| relationships.**attachments** | `array` | The associated attachments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

