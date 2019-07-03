---
description: The price object and its fields
---

# Prices

SKUs can have a price for each price list. When you create a line item, it gets the price associated with the order's the price list.

## The price object

A **price** object is returned as part of the response body of each successful [create](https://docs.commercelayer.io/resources/prices/create_price), [list](https://docs.commercelayer.io/resources/prices/list_prices), [retrieve](https://docs.commercelayer.io/resources/prices/retrieve_price), or [update](https://docs.commercelayer.io/resources/prices/update_price) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `prices` |
| **id** | `string` | The price unique identifier |
| links.**self** | `string` | The price endpoint URL |
| attributes.**currency\_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard, inherited from the associated price list. |
| attributes.**sku\_code** | `string` | The code of the associated sku. When creating a price, either a valid sku\_code or a sku relationship must be present. |
| attributes.**amount\_cents** | `integer` | The sku price amount for the associated price list, in cents. |
| attributes.**amount\_float** | `float` | The sku price amount for the associated price list, float. |
| attributes.**formatted\_amount** | `string` | The sku price amount for the associated price list, formatted. |
| attributes.**compare\_at\_amount\_cents** | `integer` | The compared price amount, in cents. Useful to display a percentage discount. |
| attributes.**compare\_at\_amount\_float** | `float` | The compared price amount, float. |
| attributes.**formatted\_compare\_at\_amount** | `string` | The compared price amount, formatted. |
| attributes.**id** | `string` | Unique identifier for the resource \(hash\). |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**price\_list** | `object` | The associated price list. |
| relationships.**sku** | `object` | The associated sku. When creating a price, either a sku relationship or a valid sku\_code must be present. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

