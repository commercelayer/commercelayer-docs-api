---
description: The promotion rule object and its fields
---

# Promotion rules



### The promotion rule object

A **promotion rule** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/promotion_rules/create_promotion_rule),
[list](https://docs.commercelayer.io/api/resources/promotion_rules/list_promotion_rules),
[retrieve](https://docs.commercelayer.io/api/resources/promotion_rules/retrieve_promotion_rule),
or [update](https://docs.commercelayer.io/api/resources/promotion_rules/update_promotion_rule) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `promotion_rules` |
| **id** | `string` | The promotion rule unique identifier |
| links.**self** | `string` | The promotion rule endpoint URL |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**promotion** | `object` | The associated promotion. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

