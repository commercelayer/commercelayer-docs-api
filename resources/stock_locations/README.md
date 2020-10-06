---
description: The stock location object and its fields
---

# Stock locations

Stock locations contain the inventory of the SKUs that are being sold. The stock location's address is the "from" address on the shipping labels.

## The stock location object

A **stock location** object is returned as part of the response body of each successful create, list, retrieve, or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `stock_locations` |
| **id** | `string` | The stock location unique identifier |
| links.**self** | `string` | The stock location endpoint URL |
| attributes.**number** | `integer` | Unique identifier for the stock location \(numeric\) |
| attributes.**name** | `string` | The stock location's internal name. |
| attributes.**label\_format** | `string` | The shipping label format for this stock location. Can be one of 'PDF', 'ZPL', 'EPL2', or 'PNG' |
| attributes.**suppress\_etd** | `boolean` | Flag it if you want to skip the electronic invoice creation when generating the customs info for this stock location shipments. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**address** | `object` | The stock location's phisical address, used as the shipping addresses "from" address. |
| relationships.**stock\_levels** | `array` | The associated stock levels. |
| relationships.**stock\_items** | `array` | The items stocked in this location. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

