---
description: The package object and its fields
---

# Packages



### The package object

A **package** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `packages` |
| **id** | `string` | The package unique identifier |
| links.**self** | `string` | The package endpoint URL |
| attributes.**name** | `string` | Unique name for the package |
| attributes.**code** | `string` | The package identifying code |
| attributes.**length** | `float` | The package length, used to automatically calculate the tax rates from the available carrier accounts. |
| attributes.**width** | `float` | The package width, used to automatically calculate the tax rates from the available carrier accounts. |
| attributes.**height** | `float` | The package height, used to automatically calculate the tax rates from the available carrier accounts. |
| attributes.**unit_of_length** | `string` | The unit of length. Can be one of 'cm', or 'in'. |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**stock_location** | `object` | The associated stock location. |
| relationships.**parcels** | `array` | The parcels associated with this package. |
| relationships.**attachments** | `array` | The associated attachments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

