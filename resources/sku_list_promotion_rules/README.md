---
description: The SKU list promotion rule object and its fields
---

# SKU list promotion rules

## The SKU list promotion rule object

A **SKU list promotion rule** object is returned as part of the response body of each successful create, list, retrieve, or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `sku_list_promotion_rules` |
| **id** | `string` | The SKU list promotion rule unique identifier |
| links.**self** | `string` | The SKU list promotion rule endpoint URL |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| attributes.**all\_skus** | `boolean` | Indicates if the rule is activated only when all of the skus of the list is also part of the order. |
| relationships.**promotion** | `object` | The associated promotion. |
| relationships.**sku\_list** | `object` | The associated sku list. |
| relationships.**skus** | `array` | The associated skus. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

