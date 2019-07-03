---
description: The shipping zone object and its fields
---

# Shipping zones

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

## The shipping zone object

A **shipping\_zone** object is returned as part of the response body of each successful [create](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/shipping_zones/create-shipping%20zone.md), [list](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/shipping_zones/list-all-shipping%20zones.md), [retrieve](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/shipping_zones/retrieve-shipping%20zone.md) or [update](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/shipping_zones/update-shipping%20zone.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `shipping_zones` |
| **id** | `string` | The shipping zone unique identifier |
| links.**self** | `string` | The shipping zone endpoint URL |
| attributes.**name** | `string` | The shipping zone's internal name. |
| attributes.**country\_code\_regex** | `string` | The regex that will be evaluated to match the shipping address country code. |
| attributes.**not\_country\_code\_regex** | `string` | The regex that will be evaluated as negative match for the shipping address country code. |
| attributes.**state\_code\_regex** | `string` | The regex that will be evaluated to match the shipping address state code. |
| attributes.**not\_state\_code\_regex** | `string` | The regex that will be evaluated as negative match for the shipping address state code. |
| attributes.**zip\_code\_regex** | `string` | The regex that will be evaluated to match the shipping address zip code. |
| attributes.**not\_zip\_code\_regex** | `string` | The regex that will be evaluated as negative match for the shipping zip country code. |
| attributes.**id** | `string` | Unique identifier for the resource \(hash\). |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

