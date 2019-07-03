---
description: The stock location object and its fields
---

# Stock locations

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

## The stock location object

A **stock\_location** object is returned as part of the response body of each successful [create](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/stock_locations/create-stock%20location.md), [list](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/stock_locations/list-all-stock%20locations.md), [retrieve](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/stock_locations/retrieve-stock%20location.md) or [update](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/stock_locations/update-stock%20location.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `stock_locations` |
| **id** | `string` | The stock location unique identifier |
| links.**self** | `string` | The stock location endpoint URL |
| attributes.**name** | `string` | The stock location's internal name. |
| attributes.**label\_format** | `string` | The shipping label format for this stock location. Can be one of 'PDF', 'ZPL', 'EPL2', or 'PNG' |
| attributes.**id** | `string` | Unique identifier for the resource \(hash\). |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**address** | `object` | The stock location's phisical address, used as the shipping addresses "from" address. |
| relationships.**stock\_levels** | `array` | The associated stock levels. |
| relationships.**stock\_items** | `array` | The items stocked in this location. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

