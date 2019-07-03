---
description: The line item option object and its fields
---

# Line item options

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

## The line item option object

A **line\_item\_option** object is returned as part of the response body of each successful [create](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/line_item_options/create-line%20item%20option.md), [list](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/line_item_options/list-all-line%20item%20options.md), [retrieve](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/line_item_options/retrieve-line%20item%20option.md) or [update](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/line_item_options/update-line%20item%20option.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `line_item_options` |
| **id** | `string` | The line item option unique identifier |
| links.**self** | `string` | The line item option endpoint URL |
| attributes.**name** | `string` | The name of the line item option. When blank, it gets populated with the name of the associated sku option. |
| attributes.**quantity** | `integer` | The line item option's quantity |
| attributes.**currency\_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard, automatically inherited from the order's market. |
| attributes.**unit\_amount\_cents** | `integer` | The unit amount of the line item option, in cents. When you add a line item option to an order, this is automatically populated from associated sku option's price. |
| attributes.**unit\_amount\_float** | `float` | The unit amount of the line item option, float. This can be useful to track the purchase on thrid party systems, e.g Google Analyitcs Enhanced Ecommerce. |
| attributes.**formatted\_unit\_amount** | `string` | The unit amount of the line item option, formatted. This can be useful to display the amount with currency in you views. |
| attributes.**total\_amount\_cents** | `integer` | The unit amount x quantity, in cents. |
| attributes.**total\_amount\_float** | `float` | The unit amount x quantity, float. This can be useful to track the purchase on thrid party systems, e.g Google Analyitcs Enhanced Ecommerce. |
| attributes.**formatted\_total\_amount** | `string` | The unit amount x quantity, formatted. This can be useful to display the amount with currency in you views. |
| attributes.**delay\_hours** | `integer` | The shipping delay that the customer can expect when adding this option \(hours\). Inherited from the associated sku option. |
| attributes.**delay\_days** | `integer` | The shipping delay that the customer can expect when adding this option \(days, rounded\). |
| attributes.**options** | `object` | Set of key-value pairs that represent the selected options. |
| attributes.**id** | `string` | Unique identifier for the resource \(hash\). |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**line\_item** | `object` | The associated line item. |
| relationships.**sku\_option** | `object` | The associated sku option. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

