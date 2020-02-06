---
description: The price object and its fields
---

# Prices

SKUs can have a price for each price list. When you create a line item, it gets the price associated with the order's price list.


### The price object

A **price** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/prices/create_price),
[list](https://docs.commercelayer.io/api/resources/prices/list_prices),
[retrieve](https://docs.commercelayer.io/api/resources/prices/retrieve_price),
or [update](https://docs.commercelayer.io/api/resources/prices/update_price) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `prices` |
| **id** | `string` | The price unique identifier |
| links.**self** | `string` | The price endpoint URL |
| attributes.**currency_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard, inherited from the associated price list. |
| attributes.**sku_code** | `string` | The code of the associated sku. When creating a price, either a valid sku_code or a sku relationship must be present. |
| attributes.**amount_cents** | `integer` | The sku price amount for the associated price list, in cents. |
| attributes.**amount_float** | `float` | The sku price amount for the associated price list, float. |
| attributes.**formatted_amount** | `string` | The sku price amount for the associated price list, formatted. |
| attributes.**compare_at_amount_cents** | `integer` | The compared price amount, in cents. Useful to display a percentage discount. |
| attributes.**compare_at_amount_float** | `float` | The compared price amount, float. |
| attributes.**formatted_compare_at_amount** | `string` | The compared price amount, formatted. |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**price_list** | `object` | The associated price list. |
| relationships.**sku** | `object` | The associated sku. When creating a price, either a sku relationship or a valid sku_code must be present. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
