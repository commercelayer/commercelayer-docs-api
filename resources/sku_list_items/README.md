---
description: The SKU list item object and its fields
---

# SKU list items

SKU list items are used to manually populate an SKU list. The position determines the order of the SKU within the associated list.

## The SKU list item object

A **SKU list item** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `sku_list_items` |
| **id** | `string` | The SKU list item unique identifier |
| links.**self** | `string` | The SKU list item endpoint URL |
| attributes.**position** | `integer` | The SKU list item's position. |
| attributes.**quantity** | `integer` | The SKU quantity for this SKU list item. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**sku\_list** | `object` | The associated SKU list. |
| relationships.**sku** | `object` | The associated sku. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

