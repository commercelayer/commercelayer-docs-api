---
description: The SKU list object and its fields
---

# SKU lists

SKU lists are used to group more SKUs, either automatically \(i.e. through a REGEX\) or manually \(i.e. by creating and sorting more SKU list items\).

## The SKU list object

A **SKU list** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `sku_lists` |
| **id** | `string` | The SKU list unique identifier |
| links.**self** | `string` | The SKU list endpoint URL |
| attributes.**name** | `string` | The SKU list's internal name. |
| attributes.**slug** | `string` | The SKU list's internal slug. |
| attributes.**description** | `string` | An internal description of the SKU list. |
| attributes.**manual** | `boolean` | Indicates if the SKU list is populated manually. |
| attributes.**sku\_code\_regex** | `string` | The regex that will be evaluated to match the SKU codes. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**skus** | `array` | The associated SKUs. |
| relationships.**sku\_list\_items** | `array` | The associated SKU list items. |
| relationships.**bundles** | `array` | The associated bundles. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

