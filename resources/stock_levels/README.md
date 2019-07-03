---
description: The stock level object and its fields
---

# Stock levels

Stock levels build a hierarchy of stock locations within an inventory model. In case an SKU is available in more stock locations, it gets shipped from those with the highest priority.

## The stock level object

A **stock level** object is returned as part of the response body of each successful [create](https://docs.commercelayer.io/api/resources/stock_levels/create_stock_level), [list](https://docs.commercelayer.io/api/resources/stock_levels/list_stock_levels), [retrieve](https://docs.commercelayer.io/api/resources/stock_levels/retrieve_stock_level), or [update](https://docs.commercelayer.io/api/resources/stock_levels/update_stock_level) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `stock_levels` |
| **id** | `string` | The stock level unique identifier |
| links.**self** | `string` | The stock level endpoint URL |
| attributes.**priority** | `integer` | The stock location priority within the associated invetory model. |
| attributes.**on\_hold** | `boolean` | Indicates if the shipment should be put on hold if fulfilled from the associated stock location. This is useful to manage use cases like back-orders, pre-orders or personalized orders that need to be customized before being fulfilled. |
| attributes.**id** | `string` | Unique identifier for the resource \(hash\). |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**stock\_location** | `object` | The associated stock location. |
| relationships.**inventory\_model** | `object` | The associated inventory model. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

