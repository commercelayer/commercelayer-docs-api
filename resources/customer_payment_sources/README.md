---
description: The customer payment source object and its fields
---

# Customer payment sources

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

## The customer payment source object

A **customer\_payment\_source** object is returned as part of the response body of each successful [create](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/customer_payment_sources/create-customer%20payment%20source.md), [list](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/customer_payment_sources/list-all-customer%20payment%20sources.md), [retrieve](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/customer_payment_sources/retrieve-customer%20payment%20source.md) or [update](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/customer_payment_sources/update-customer%20payment%20source.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `customer_payment_sources` |
| **id** | `string` | The customer payment source unique identifier |
| links.**self** | `string` | The customer payment source endpoint URL |
| attributes.**name** | `string` | Returns the associated payment source's name |
| attributes.**id** | `string` | Unique identifier for the resource \(hash\). |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**customer** | `object` | The associated customer. |
| relationships.**payment\_source** | `object` | The associated payment source \(i.e. credit card\). |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

