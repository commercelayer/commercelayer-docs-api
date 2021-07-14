---
description: The taxjar account object and its fields
---

# Taxjar accounts

Configure your Taxjar account to automatically compute tax calculations for the orders of the associated market.


### The taxjar account object

A **taxjar account** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `taxjar_accounts` |
| **id** | `string` | The taxjar account unique identifier |
| links.**self** | `string` | The taxjar account endpoint URL |
| attributes.**name** | `string` | The tax calculator's internal name. |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| attributes.**api_key** | `string` | The TaxJar account API key. |
| relationships.**tax_categories** | `array` | The associated tax categories. |
| relationships.**markets** | `array` | The associated markets. |
| relationships.**attachments** | `array` | The associated attachments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

