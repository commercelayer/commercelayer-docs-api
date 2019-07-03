---
description: The price list object and its fields
---

# Price lists

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

## The price list object

A **price\_list** object is returned as part of the response body of each successful [create](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/price_lists/create-price%20list.md), [list](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/price_lists/list-all-price%20lists.md), [retrieve](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/price_lists/retrieve-price%20list.md) or [update](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/price_lists/update-price%20list.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `price_lists` |
| **id** | `string` | The price list unique identifier |
| links.**self** | `string` | The price list endpoint URL |
| attributes.**name** | `string` | The market's internal name |
| attributes.**currency\_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard. |
| attributes.**tax\_included** | `boolean` | Indiceates if the associated prices include taxes. |
| attributes.**id** | `string` | Unique identifier for the resource \(hash\). |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**prices** | `array` | The associated prices. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

