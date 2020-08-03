---
description: The coupon codes promotion rule object and its fields
---

# Coupon codes promotion rules



### The coupon codes promotion rule object

A **coupon codes promotion rule** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/coupon_codes_promotion_rules/create_coupon_codes_promotion_rule),
[list](https://docs.commercelayer.io/api/resources/coupon_codes_promotion_rules/list_coupon_codes_promotion_rules),
[retrieve](https://docs.commercelayer.io/api/resources/coupon_codes_promotion_rules/retrieve_coupon_codes_promotion_rule),
or [update](https://docs.commercelayer.io/api/resources/coupon_codes_promotion_rules/update_coupon_codes_promotion_rule) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `coupon_codes_promotion_rules` |
| **id** | `string` | The coupon codes promotion rule unique identifier |
| links.**self** | `string` | The coupon codes promotion rule endpoint URL |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**promotion** | `object` | The associated promotion. |
| relationships.**coupons** | `array` | The associated coupons. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

