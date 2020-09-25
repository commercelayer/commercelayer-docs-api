---
description: The coupon object and its fields
---

# Coupons

## The coupon object

A **coupon** object is returned as part of the response body of each successful [create](https://docs.commercelayer.io/api/resources/coupons/create_coupon), [list](https://docs.commercelayer.io/api/resources/coupons/list_coupons), [retrieve](https://docs.commercelayer.io/api/resources/coupons/retrieve_coupon), or [update](https://docs.commercelayer.io/api/resources/coupons/update_coupon) API call.

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

