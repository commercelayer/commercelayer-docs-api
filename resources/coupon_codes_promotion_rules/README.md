---
description: The coupon codes promotion rule object and its fields
---

# Coupon codes promotion rules

Commerce Layer provides a promotional engine built on top of two main resources: [promotions](https://docs.commercelayer.io/api/resources/promotions) and [promotion rules](https://docs.commercelayer.io/api/resources/promotion_rules). Coupon code promotions rules are used to link a promotion to a specific [coupon](https://docs.commercelayer.io/api/resources/coupons) so that the promotion is triggered only based on the coupon code.

## The coupon codes promotion rule object

A **coupon codes promotion rule** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `coupon_codes_promotion_rules` |
| **id** | `string` | The coupon codes promotion rule unique identifier |
| links.**self** | `string` | The coupon codes promotion rule endpoint URL |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**promotion** | `object` | The associated promotion. |
| relationships.**coupons** | `array` | The associated coupons. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

