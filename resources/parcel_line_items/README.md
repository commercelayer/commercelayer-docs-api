---
description: The parcel line item object and its fields
---

# Parcel line items

## The parcel line item object

A **parcel line item** object is returned as part of the response body of each successful create, list, retrieve, or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `parcel_line_items` |
| **id** | `string` | The parcel line item unique identifier |
| links.**self** | `string` | The parcel line item endpoint URL |
| attributes.**sku\_code** | `string` | The code of the sku of the associated shipment\_line\_item. |
| attributes.**quantity** | `integer` | The parcel line item quantity. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**parcel** | `object` | The associated parcel. |
| relationships.**shipment\_line\_item** | `object` | The associated shipment line item. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

