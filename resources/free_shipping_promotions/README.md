---
description: The free shipping promotion object and its fields
---

# Free shipping promotions

Commerce Layer provides a promotional engine built on top of two main resources: [promotions](https://docs.commercelayer.io/api/resources/promotions) and [promotion rules](https://docs.commercelayer.io/api/resources/promotion_rules). Free shipping promotions are defined by market and — when triggered — are responsible for setting to zero the shipping amount of the market orders. Within the time window given by their activation and expiration dates, free shipping promotions that have not reached their total usage limit are considered active. If no promotion rule is associated with an active free shipping promotion, the related discount is applied to all the orders of the market in scope. Otherwise, if one or more promotion rules are defined, the promotion is triggered only when it matches all of them.


### The free shipping promotion object

A **free shipping promotion** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `free_shipping_promotions` |
| **id** | `string` | The free shipping promotion unique identifier |
| links.**self** | `string` | The free shipping promotion endpoint URL |
| attributes.**name** | `string` | The promotion's internal name. |
| attributes.**starts_at** | `datetime` | The activation date/time of this promotion. |
| attributes.**expires_at** | `datetime` | The expiration date/time of this promotion (must be after starts_at). |
| attributes.**total_usage_limit** | `integer` | The total number of times this promotion can be applied. |
| attributes.**total_usage_count** | `integer` | The number of times this promotion has been applied. |
| attributes.**active** | `boolean` | Indicates if the promotion is active. |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**market** | `object` | The associated market. |
| relationships.**promotion_rules** | `array` | The associated promotion rules. |
| relationships.**order_amount_promotion_rule** | `object` | The associated order amount promotion rule. |
| relationships.**sku_list_promotion_rule** | `object` | The associated sku list promotion rule. |
| relationships.**coupon_codes_promotion_rule** | `object` | The associated coupon codes promotion rule. |
| relationships.**attachments** | `array` | The associated attachments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

