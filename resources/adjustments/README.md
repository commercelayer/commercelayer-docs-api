---
description: The adjustment object and its fields
---

# Adjustments

Adjustments are arbitrary objects that can be used to change the total amount of an order by any value, either greater or lower than zero. To add an adjustment to an order, you first need to create the adjustment and then create a line item that references it.

## The adjustment object

An **adjustment** object is returned as part of the response body of each successful [create](https://docs.commercelayer.io/api/resources/adjustments/create_adjustment), [list](https://docs.commercelayer.io/api/resources/adjustments/list_adjustments), [retrieve](https://docs.commercelayer.io/api/resources/adjustments/retrieve_adjustment), or [update](https://docs.commercelayer.io/api/resources/adjustments/update_adjustment) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `adjustments` |
| **id** | `string` | The adjustment unique identifier |
| links.**self** | `string` | The adjustment endpoint URL |
| attributes.**name** | `string` | The adjustment name |
| attributes.**currency\_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard. |
| attributes.**amount\_cents** | `integer` | The adjustment amount, in cents. |
| attributes.**amount\_float** | `float` | The adjustment amount, float. |
| attributes.**formatted\_amount** | `string` | The adjustment amount, formatted. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

