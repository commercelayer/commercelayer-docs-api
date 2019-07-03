---
description: The line item option object and its fields
---

# Line item options

Create a line item option if you want to add one or more SKU options to a line item.
The SKU options cost is automatically added to the line item's amount.


### The line item option object

A **line item option** object is returned as part of the response body of each successful [create](create-line item option.md), [list](list-all-line item options.md), [retrieve](retrieve-line item option.md) or [update](update-line item option.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `line_item_options` |
| **id** | `string` | The line item option unique identifier |
| links.**self** | `string` | The line item option endpoint URL |
| attributes.**name** | `string` | The name of the line item option. When blank, it gets populated with the name of the associated sku option. |
| attributes.**quantity** | `integer` | The line item option's quantity |
| attributes.**currency_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard, automatically inherited from the order's market. |
| attributes.**unit_amount_cents** | `integer` | The unit amount of the line item option, in cents. When you add a line item option to an order, this is automatically populated from associated sku option's price. |
| attributes.**unit_amount_float** | `float` | The unit amount of the line item option, float. This can be useful to track the purchase on thrid party systems, e.g Google Analyitcs Enhanced Ecommerce. |
| attributes.**formatted_unit_amount** | `string` | The unit amount of the line item option, formatted. This can be useful to display the amount with currency in you views. |
| attributes.**total_amount_cents** | `integer` | The unit amount x quantity, in cents. |
| attributes.**total_amount_float** | `float` | The unit amount x quantity, float. This can be useful to track the purchase on thrid party systems, e.g Google Analyitcs Enhanced Ecommerce. |
| attributes.**formatted_total_amount** | `string` | The unit amount x quantity, formatted. This can be useful to display the amount with currency in you views. |
| attributes.**delay_hours** | `integer` | The shipping delay that the customer can expect when adding this option (hours). Inherited from the associated sku option. |
| attributes.**delay_days** | `integer` | The shipping delay that the customer can expect when adding this option (days, rounded). |
| attributes.**options** | `object` | Set of key-value pairs that represent the selected options. |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**line_item** | `object` | The associated line item. |
| relationships.**sku_option** | `object` | The associated sku option. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
