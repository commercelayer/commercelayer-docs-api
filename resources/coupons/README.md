---
description: The coupon object and its fields
---

# Coupons

Commerce Layer provides a promotional engine built on top of two main resources: [promotions](https://docs.commercelayer.io/api/resources/promotions) and [promotion rules](https://docs.commercelayer.io/api/resources/promotion_rules). Coupons have to be associated with [coupon code](https://docs.commercelayer.io/api/resources/coupon_codes_promotion_rules) promotions rules so that a promotion is triggered when customers enter a specific coupon code at checkout. The coupon can be used multiple times and it is considered valid until its usage count exceeds the threshold set by its usage limit. Set the `usage_limit` attribute to `1` if you want the code to be used just once.

## The coupon object

A **coupon** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `coupons` |
| **id** | `string` | The coupon unique identifier |
| links.**self** | `string` | The coupon endpoint URL |
| attributes.**code** | `string` | The coupon code, that uniquely identifies the coupon within the promotion rule. |
| attributes.**usage\_limit** | `integer` | The total number of times this coupon can be used. |
| attributes.**usage\_count** | `integer` | The number of times this coupon has been used. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**promotion\_rule** | `object` | The associated promotion rule. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

