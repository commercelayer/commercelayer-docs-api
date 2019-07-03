---
description: The stock location object and its fields
---

# Stock locations

Stock locations contain the inventory of the SKUs that are being sold.
The stock location's address is the "from" address on the shipping labels ([learn more](https://commercelayer.io/glossary/stock_location/)).


### The stock location object

A **stock location** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/resources/stock_locations/create_stock_location),
[list](https://docs.commercelayer.io/resources/stock_locations/list_stock_locations),
[retrieve](https://docs.commercelayer.io/resources/stock_locations/retrieve_stock_location),
or [update](https://docs.commercelayer.io/resources/stock_locations/update_stock_location) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `stock_locations` |
| **id** | `string` | The stock location unique identifier |
| links.**self** | `string` | The stock location endpoint URL |
| attributes.**name** | `string` | The stock location's internal name. |
| attributes.**label_format** | `string` | The shipping label format for this stock location. Can be one of 'PDF', 'ZPL', 'EPL2', or 'PNG' |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**address** | `object` | The stock location's phisical address, used as the shipping addresses "from" address. |
| relationships.**stock_levels** | `array` | The associated stock levels. |
| relationships.**stock_items** | `array` | The items stocked in this location. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
