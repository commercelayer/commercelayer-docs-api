---
description: The delivery lead time object and its fields
---

# Delivery lead times

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

## The delivery lead time object

A **delivery\_lead\_time** object is returned as part of the response body of each successful [create](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/delivery_lead_times/create-delivery%20lead%20time.md), [list](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/delivery_lead_times/list-all-delivery%20lead%20times.md), [retrieve](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/delivery_lead_times/retrieve-delivery%20lead%20time.md) or [update](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/delivery_lead_times/update-delivery%20lead%20time.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `delivery_lead_times` |
| **id** | `string` | The delivery lead time unique identifier |
| links.**self** | `string` | The delivery lead time endpoint URL |
| attributes.**min\_hours** | `integer` | The delivery lead minimum time \(in hours\) when shipping from the associated stock location with the associated shipping method. |
| attributes.**max\_hours** | `integer` | The delivery lead maximun time \(in hours\) when shipping from the associated stock location with the associated shipping method. |
| attributes.**min\_days** | `integer` | The delivery lead minimum time, in days \(rounded\) |
| attributes.**max\_days** | `integer` | The delivery lead maximun time, in days \(rounded\) |
| attributes.**id** | `string` | Unique identifier for the resource \(hash\). |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**stock\_location** | `object` | The associated stock location. |
| relationships.**shipping\_method** | `object` | The associated shipping method. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

