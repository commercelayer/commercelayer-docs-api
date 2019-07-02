---
description: The price object and its fields
---

# Prices

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

### The Price object

A price object is returned as part of the response body of each successful [create](create-price.md), [list](list-all-prices.md), [retrieve](retrieve-price.md) or [update](update-price.md) API call.

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
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**price_list** | `object` | The associated price list. |
| relationships.**sku** | `object` | The associated sku. When creating a price, either a sku relationship or a valid sku_code must be present. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
