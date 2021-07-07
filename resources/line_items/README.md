---
description: The line item object and its fields
---

# Line items

Create a line item if you want to add an SKU to an order. Other types of line items are automatically created to add a shipping cost to the order or to apply a discount. The sum of all line item amounts makes the order's total, split into subtotal, taxes, and discount. The order object includes all the data you need. You never need to make any calculations on your application.

## The line item object

A **line item** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `line_items` |
| **id** | `string` | The line item unique identifier |
| links.**self** | `string` | The line item endpoint URL |
| attributes.**sku\_code** | `string` | The code of the associated sku. |
| attributes.**bundle\_code** | `string` | The code of the associated bundle. |
| attributes.**quantity** | `integer` | The line item quantity. |
| attributes.**\_external\_price** | `boolean, value is 'false'` | When creating a new line item, set this attribute to '1' if you want to inject the unit\_amount\_cents price from an external source. |
| attributes.**\_update\_quantity** | `boolean, value is 'true'` | When creating a new line item, set this attribute to '1' if you want to update the line item quantity \(if present\) instead of creating a new line item for the same sku. |
| attributes.**currency\_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard, automatically inherited from the order's market. |
| attributes.**unit\_amount\_cents** | `integer` | The unit amount of the line item, in cents. Can be specified without an item, otherwise is automatically populated from the price list associated to the order's market. |
| attributes.**unit\_amount\_float** | `float` | The unit amount of the line item, float. This can be useful to track the purchase on thrid party systems, e.g Google Analyitcs Enhanced Ecommerce. |
| attributes.**formatted\_unit\_amount** | `string` | The unit amount of the line item, formatted. This can be useful to display the amount with currency in you views. |
| attributes.**options\_amount\_cents** | `integer` | The options amount of the line item, in cents. |
| attributes.**options\_amount\_float** | `float` | The options amount of the line item, float. |
| attributes.**formatted\_options\_amount** | `string` | The options amount of the line item, formatted. |
| attributes.**discount\_cents** | `integer` | The discount applied to the line item, in cents. When you apply a discount to an order, this is automatically calculated basing on the line item total\_amount\_cents value. |
| attributes.**discount\_float** | `float` | The discount applied to the line item, float. When you apply a discount to an order, this is automatically calculated basing on the line item total\_amount\_cents value. |
| attributes.**formatted\_discount** | `string` | The discount applied to the line item, fromatted. When you apply a discount to an order, this is automatically calculated basing on the line item total\_amount\_cents value. |
| attributes.**total\_amount\_cents** | `integer` | Calculated as unit amount x quantity + options amount, in cents. |
| attributes.**total\_amount\_float** | `float` | Calculated as unit amount x quantity + options amount, float. This can be useful to track the purchase on thrid party systems, e.g Google Analyitcs Enhanced Ecommerce. |
| attributes.**formatted\_total\_amount** | `string` | Calculated as unit amount x quantity + options amount, formatted. This can be useful to display the amount with currency in you views. |
| attributes.**tax\_amount\_cents** | `integer` | Calculated as total amount cents - discount cent \* tax rate, in cents. |
| attributes.**tax\_amount\_float** | `float` | Calculated as total amount cents - discount cent \* tax rate, float. |
| attributes.**formatted\_tax\_amount** | `string` | Calculated as total amount cents - discount cent \* tax rate, formatted. |
| attributes.**name** | `string` | The name of the line item. When blank, it gets populated with the name of the associated item \(if present\). |
| attributes.**image\_url** | `string` | The image\_url of the line item. When blank, it gets populated with the image\_url of the associated item \(if present, sku only\). |
| attributes.**discount\_breakdown** | `object` | The discount breakdown for this line item \(if calculated\). |
| attributes.**tax\_rate** | `float` | The tax rate for this line item \(if calculated\). |
| attributes.**tax\_breakdown** | `object` | The tax breakdown for this line item \(if calculated\). |
| attributes.**item\_type** | `string` | The type of the associate item. Can be one of 'sku', 'bundle', 'shipment', 'payment\_method', 'adjustment', 'gift\_card', or a valid promotion type. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**order** | `object` | The associated order. |
| relationships.**item** | `object` | The polymorphic item associated to the line item. Can be a 'sku', a 'shipment', a 'payment\_method', an 'adjustment', a 'gift\_card', or a valid promotion type. |
| relationships.**line\_item\_options** | `array` | The associated line item options. |
| relationships.**shipment\_line\_items** | `array` | The associated shipment line items. |
| relationships.**stock\_line\_items** | `array` | The associated stock line items. |
| relationships.**stock\_transfers** | `array` | The associated stock transfers. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

