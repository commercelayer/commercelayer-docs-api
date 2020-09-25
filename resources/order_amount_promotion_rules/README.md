---
description: The order amount promotion rule object and its fields
---

# Order amount promotion rules

## The order amount promotion rule object

An **order amount promotion rule** object is returned as part of the response body of each successful [create](https://docs.commercelayer.io/api/resources/order_amount_promotion_rules/create_order_amount_promotion_rule), [list](https://docs.commercelayer.io/api/resources/order_amount_promotion_rules/list_order_amount_promotion_rules), [retrieve](https://docs.commercelayer.io/api/resources/order_amount_promotion_rules/retrieve_order_amount_promotion_rule), or [update](https://docs.commercelayer.io/api/resources/order_amount_promotion_rules/update_order_amount_promotion_rule) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `order_amount_promotion_rules` |
| **id** | `string` | The order amount promotion rule unique identifier |
| links.**self** | `string` | The order amount promotion rule endpoint URL |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| attributes.**order\_amount\_cents** | `integer` | Apply the promotion only when order is over this amount, in cents. |
| attributes.**order\_amount\_float** | `float` | Apply the promotion only when order is over this amount, float. |
| attributes.**formatted\_order\_amount** | `string` | Apply the promotion only when order is over this amount, formatted. |
| relationships.**promotion** | `object` | The associated promotion. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

