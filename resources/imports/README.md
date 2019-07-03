---
description: The import object and its fields
---

# Imports

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

## The import object

An **import** object is returned as part of the response body of each successful [create](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/imports/create-import.md), [list](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/imports/list-all-imports.md), [retrieve](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/imports/retrieve-import.md) or [update](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/imports/update-import.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `imports` |
| **id** | `string` | The import unique identifier |
| links.**self** | `string` | The import endpoint URL |
| attributes.**resource\_type** | `string` | The type of resource being imported. One of 'skus', 'prices', or 'stock\_items' |
| attributes.**parent\_resource\_id** | `integer` | The ID of the parent resource. It can be the 'shipping\_category\_id' for 'skus', the 'price\_list\_id' for 'prices', or the 'stock\_location\_id' for 'stock\_items' |
| attributes.**status** | `string` | The import job status. One of 'pending' \(default\), 'started', or 'completed' |
| attributes.**started\_at** | `datetime` | Time at which the import was started. |
| attributes.**completed\_at** | `datetime` | Time at which the import was completed. |
| attributes.**inputs** | `object` | Array of objects representing the resources that are being imported. |
| attributes.**errors\_count** | `integer` | Indicates the number of import errors, if any. |
| attributes.**warnings\_count** | `integer` | Indicates the number of import warnings, if any. |
| attributes.**destroyed\_count** | `integer` | Indicates the number of records that have been destroyed, if any. |
| attributes.**errors\_log** | `object` | Contains the import errors, if any. |
| attributes.**warnings\_log** | `object` | Contains the import warnings, if any. |
| attributes.**cleanup\_records** | `boolean` | Indicates if the import should cleanup records that are not included in the inputs array. |
| attributes.**id** | `string` | Unique identifier for the resource \(hash\). |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

