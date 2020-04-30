---
description: The SKU list object and its fields
---

# Sku lists



### The SKU list object

A **SKU list** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/sku_lists/create_sku_list),
[list](https://docs.commercelayer.io/api/resources/sku_lists/list_sku_lists),
[retrieve](https://docs.commercelayer.io/api/resources/sku_lists/retrieve_sku_list),
or [update](https://docs.commercelayer.io/api/resources/sku_lists/update_sku_list) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `sku_lists` |
| **id** | `string` | The SKU list unique identifier |
| links.**self** | `string` | The SKU list endpoint URL |
| attributes.**name** | `string` | The sku list's internal name. |
| attributes.**slug** | `string` | The sku list's internal slug. |
| attributes.**description** | `string` | An internal description of the sku list. |
| attributes.**manual** | `boolean` | Indicates if the sku list is populated manually. |
| attributes.**sku_code_regex** | `string` | The regex that will be evaluated to match the sku codes. |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**skus** | `array` | The associated skus. |
| relationships.**sku_list_items** | `array` | The associated sku list items. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

