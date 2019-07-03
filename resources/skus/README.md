---
description: The SKU object and its fields
---

# Skus

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

## The SKU object

An **sku** object is returned as part of the response body of each successful [create](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/skus/create-SKU.md), [list](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/skus/list-all-SKUs.md), [retrieve](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/skus/retrieve-SKU.md) or [update](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/skus/update-SKU.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `skus` |
| **id** | `string` | The SKU unique identifier |
| links.**self** | `string` | The SKU endpoint URL |
| attributes.**code** | `string` | The sku code, that uniquely identifies the sku within the organization. |
| attributes.**name** | `string` | The internal name of the sku. |
| attributes.**description** | `string` | An internal description of the sku. |
| attributes.**image\_url** | `string` | The URL of an image that represents the sku. |
| attributes.**tag\_names** | `string` | A comma separated list of tags. |
| attributes.**pieces\_per\_pack** | `integer` | The number of pieces that compose the sku. This is useful to describe sets and bundles. |
| attributes.**weight** | `float` | The weight of the sku. If present, it will be used to calculate the shipping rates. |
| attributes.**unit\_of\_weight** | `string` | Can be one of 'gr', or 'oz' |
| attributes.**inventory** | `object` | Aggregated information about the SKU's inventory. Returned only when retrieving a single SKU with a Channel application. |
| attributes.**id** | `string` | Unique identifier for the resource \(hash\). |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**shipping\_category** | `object` | The sku's shipping category |
| relationships.**prices** | `array` | The list of prices associated with the sku. |
| relationships.**stock\_items** | `array` | The list of stock items associated with the sku. |
| relationships.**delivery\_lead\_times** | `array` | The list of delivery lead times associated with the sku. |
| relationships.**sku\_options** | `array` | The list of sku options available for the sku. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

