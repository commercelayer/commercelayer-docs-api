---
description: The external promotion object and its fields
---

# External promotions

Commerce Layer provides a promotional engine built on top of two main resources: [promotions](https://docs.commercelayer.io/api/resources/promotions) and [promotion rules](https://docs.commercelayer.io/api/resources/promotion_rules). Besides the promotion types that are supported out-of-the-box Commerce Layer lets you integrate any kind of promotional engine as an external promotion. External promotions are defined by market and are responsible for adding the externally computed discount to the market orders. When an external promotion activates, Commerce Layer triggers a POST request to the promotion URL endpoint, sending the order payload \(including its line items\) in the request body. The external service response \(or error\) must match the format described in [this example](https://docs.commercelayer.io/api/external-resources/external-promotions).

Within the time window given by their activation and expiration dates, external promotions that have not reached their total usage limit are considered active. If no promotion rule is associated with an active external promotion, the computed discount is applied to all the orders of the market in scope. Otherwise, if one or more promotion rules are defined, the promotion is triggered only when it matches all of them.

## The external promotion object

An **external promotion** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `external_promotions` |
| **id** | `string` | The external promotion unique identifier |
| links.**self** | `string` | The external promotion endpoint URL |
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
| attributes.**promotion\_url** | `string` | The URL to the service that will compute the discount. |
| relationships.**market** | `object` | The associated market. |
| relationships.**promotion\_rules** | `array` | The associated promotion rules. |
| relationships.**order\_amount\_promotion\_rule** | `object` | The associated order amount promotion rule. |
| relationships.**sku\_list\_promotion\_rule** | `object` | The associated sku list promotion rule. |
| relationships.**coupon\_codes\_promotion\_rule** | `object` | The associated coupon codes promotion rule. |
| relationships.**attachments** | `array` | The associated attachments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

