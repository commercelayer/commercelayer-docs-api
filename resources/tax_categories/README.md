---
description: The tax category object and its fields
---

# Tax categories

Create a tax category for an SKU that has special taxation. Specify a valid tax code for the associated tax calculator (currently supported by Avalara and Taxjar).


### The tax category object

A **tax category** object is returned as part of the response body of each successful create, list, retrieve, or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `tax_categories` |
| **id** | `string` | The tax category unique identifier |
| links.**self** | `string` | The tax category endpoint URL |
| attributes.**code** | `string` | The tax category identifier code, specific for a particular tax calculator. |
| attributes.**sku_code** | `string` | The code of the associated sku |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**sku** | `object` | The associated sku. |
| relationships.**tax_calculator** | `object` | The associated tax calculator. |
| relationships.**attachments** | `array` | The associated attachments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

