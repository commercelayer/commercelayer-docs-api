---
description: The promotion rule object and its fields
---

# Promotion rules

Commerce Layer provides a promotional engine built on top of two main resources: [promotions](https://docs.commercelayer.io/api/resources/promotions) and promotion rules. If one or more promotion rules are defined, the promotion is triggered only when it matches all of them. Otherwise, if no promotion rule is associated with an active promotion, the related discount is applied to all the orders of the market in scope.

At the moment [order amount](https://docs.commercelayer.io/api/resources/order_amount_promotion_rules), [SKU list](https://docs.commercelayer.io/api/resources/sku_list_promotion_rules), and [coupon code](https://docs.commercelayer.io/api/resources/coupon_codes_promotion_rules) promotion rules are available (more to come).


### The promotion rule object

A **promotion rule** object is returned as part of the response body of each successful list API call.

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

