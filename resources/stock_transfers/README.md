---
description: The stock transfer object and its fields
---

# Stock transfers

An order can be configured to ship from a single stock location \(i.e. primary\). In this scenario the number of shipments is minimized by creating one or more stock transfers from the stock location where the items are available to the primary one. Shipping categories are still honored, by creating different shipments. Stock transfers can also be created outside of the order scope, in such case they have no relationships with shipments and line items.

## The stock transfer object

A **stock transfer** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `stock_transfers` |
| **id** | `string` | The stock transfer unique identifier |
| links.**self** | `string` | The stock transfer endpoint URL |
| attributes.**sku\_code** | `string` | The code of the associated sku. |
| attributes.**status** | `string` | The stock transfer status, one of 'draft', 'upcoming', 'picking', 'in\_transit', 'completed', or 'cancelled' |
| attributes.**quantity** | `integer` | The stock quantity to be transferred from the origin stock location to destination one |
| attributes.**completed\_at** | `datetime` | Time at which the stock transfer was completed. |
| attributes.**cancelled\_at** | `datetime` | Time at which the stock transfer was cancelled. |
| attributes.**\_upcoming** | `boolean, value is 'true'` | Send this attribute if you want to mark this stock transfer as upcoming. |
| attributes.**\_picking** | `boolean, value is 'true'` | Send this attribute if you want to start picking this stock transfer. |
| attributes.**\_in\_transit** | `boolean, value is 'true'` | Send this attribute if you want to mark this stock transfer as in transit. |
| attributes.**\_complete** | `boolean, value is 'true'` | Send this attribute if you want to complete this stock transfer. |
| attributes.**\_cancel** | `boolean, value is 'true'` | Send this attribute if you want to cancel this stock transfer. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**sku** | `object` | The associated sku. |
| relationships.**origin\_stock\_location** | `object` | The origin stock location. |
| relationships.**destination\_stock\_location** | `object` | The destination stock location. |
| relationships.**shipment** | `object` | The associated shipment. |
| relationships.**line\_item** | `object` | The associated line\_item. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

