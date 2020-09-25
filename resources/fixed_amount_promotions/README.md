---
description: The fixed amount promotion object and its fields
---

# Fixed amount promotions

## The fixed amount promotion object

A **fixed amount promotion** object is returned as part of the response body of each successful [create](https://docs.commercelayer.io/api/resources/fixed_amount_promotions/create_fixed_amount_promotion), [list](https://docs.commercelayer.io/api/resources/fixed_amount_promotions/list_fixed_amount_promotions), [retrieve](https://docs.commercelayer.io/api/resources/fixed_amount_promotions/retrieve_fixed_amount_promotion), or [update](https://docs.commercelayer.io/api/resources/fixed_amount_promotions/update_fixed_amount_promotion) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `fixed_amount_promotions` |
| **id** | `string` | The fixed amount promotion unique identifier |
| links.**self** | `string` | The fixed amount promotion endpoint URL |
| attributes.**name** | `string` | The promotion's internal name. |
| attributes.**starts\_at** | `datetime` | The activation date/time of this promotion. |
| attributes.**expires\_at** | `datetime` | The expiration date/time of this promotion \(must be after starts\_at\). |
| attributes.**total\_usage\_limit** | `integer` | The total number of times this promotion can be applied. |
| attributes.**total\_usage\_count** | `integer` | The number of times this promotion has been applied. |
| attributes.**active** | `boolean` | Indicates if the promotion is active. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| attributes.**fixed\_amount\_cents** | `integer` | The discount fixed amount to be applied, in cents |
| attributes.**fixed\_amount\_float** | `float` | The discount fixed amount to be applied, float. |
| attributes.**formatted\_fixed\_amount** | `string` | The discount fixed amount to be applied, formatted. |
| relationships.**market** | `object` | The associated market. |
| relationships.**promotion\_rules** | `array` | The associated promotion rules. |
| relationships.**order\_amount\_promotion\_rule** | `object` | The associated order amount promotion rule. |
| relationships.**sku\_list\_promotion\_rule** | `object` | The associated sku list promotion rule. |
| relationships.**coupon\_codes\_promotion\_rule** | `object` | The associated coupon codes promotion rule. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
