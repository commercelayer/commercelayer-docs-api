---
description: The stock item object and its fields
---

# Stock items

A stock item keeps the available inventory of an SKU in a given stock location.
When you create a line item, the associated SKU must be available in one of the market's stock locations.
When you place an order, the stock item quantities get decremented.
When an order is canceled, or a return is approved, the stock item quantities get incremented.


### The stock item object

A **stock item** object is returned as part of the response body of each successful
[create](/api-reference/resources/stock_items/create_stock_item),
[list](/api-reference/resources/stock_items/list_stock_items),
[retrieve](/api-reference/resources/stock_items/retrieve_stock_item),
or [update](/api-reference/resources/stock_items/update_stock_item) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `stock_items` |
| **id** | `string` | The stock item unique identifier |
| links.**self** | `string` | The stock item endpoint URL |
| attributes.**sku_code** | `string` | The code of the associated sku. |
| attributes.**quantity** | `integer` | The stock item quantity. |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**stock_location** | `object` | The associated stock location. |
| relationships.**sku** | `object` | The associated stock sku. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
