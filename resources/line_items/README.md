---
description: The line item object and its fields
---

# Line items

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

### The line item object

A **line item** object is returned as part of the response body of each successful [create](create-line item.md), [list](list-all-line items.md), [retrieve](retrieve-line item.md) or [update](update-line item.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `line_items` |
| **id** | `string` | The line item unique identifier |
| links.**self** | `string` | The line item endpoint URL |
| attributes.**sku_code** | `string` | The code of the associated sku |
| attributes.**quantity** | `integer` | The line item quantity |
| attributes.**_update_quantity** | `integer, value is '1'` | When creating a new line item, set this attribute to '1' if you want to update the line item quantity (if present) instead of creating a new line item for the same sku. |
| attributes.**currency_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard, automatically inherited from the order's market. |
| attributes.**unit_amount_cents** | `integer` | The unit amount of the line item, in cents. When you add a line item to an order, this is automatically populated from the price list associated to the order's market. |
| attributes.**unit_amount_float** | `float` | The unit amount of the line item, float. This can be useful to track the purchase on thrid party systems, e.g Google Analyitcs Enhanced Ecommerce. |
| attributes.**formatted_unit_amount** | `string` | The unit amount of the line item, formatted. This can be useful to display the amount with currency in you views. |
| attributes.**options_amount_cents** | `integer` | The options amount of the line item, in cents. |
| attributes.**options_amount_float** | `float` | The options amount of the line item, float. |
| attributes.**formatted_options_amount** | `string` | The options amount of the line item, formatted. |
| attributes.**total_amount_cents** | `integer` | Calculated as unit amount x quantity + options amount, in cents. |
| attributes.**total_amount_float** | `float` | Calculated as unit amount x quantity + options amount, float. This can be useful to track the purchase on thrid party systems, e.g Google Analyitcs Enhanced Ecommerce. |
| attributes.**formatted_total_amount** | `string` | Calculated as unit amount x quantity + options amount, formatted. This can be useful to display the amount with currency in you views. |
| attributes.**name** | `string` | The name of the line item. When blank, it gets populated with the name of the associated item (if present). |
| attributes.**image_url** | `string` | The image_url of the line item. When blank, it gets populated with the image_url of the associated item (if present, sku only). |
| attributes.**tax_rate** | `float` | The tax rate for this line item (if calculated). |
| attributes.**tax_breakdown** | `object` | The tax breakdown for this line item (if calculated). |
| attributes.**item_type** | `string` | The type of the associate item. Can be one of 'sku', 'shipment', 'payment_method', or 'promotion' |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**order** | `object` | The associated order. |
| relationships.**item** | `object` | The polymorphic item associated to the line item. Can be a sku, a shipment, a payment_method or a promotion. |
| relationships.**line_item_options** | `array` | The associated line item options. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
