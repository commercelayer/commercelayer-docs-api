---
description: The stock item object and its fields
---

# Stock items

A stock item keeps the available inventory of an SKU in a given stock location. When you create a line item, the associated SKU must be available in one of the market's stock locations. When you place an order, the stock item quantities get decremented. When an order is canceled, or a return is approved, the stock item quantities get incremented.

## The stock item object

A **stock item** object is returned as part of the response body of each successful [create](https://docs.commercelayer.io/api/resources/stock_items/create_stock_item), [list](https://docs.commercelayer.io/api/resources/stock_items/list_stock_items), [retrieve](https://docs.commercelayer.io/api/resources/stock_items/retrieve_stock_item), or [update](https://docs.commercelayer.io/api/resources/stock_items/update_stock_item) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `stock_items` |
| **id** | `string` | The stock item unique identifier |
| links.**self** | `string` | The stock item endpoint URL |
| attributes.**sku\_code** | `string` | The code of the associated sku. |
| attributes.**quantity** | `integer` | The stock item quantity. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**stock\_location** | `object` | The associated stock location. |
| relationships.**sku** | `object` | The associated stock sku. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

