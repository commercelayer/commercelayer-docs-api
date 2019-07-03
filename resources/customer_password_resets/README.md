---
description: The customer password reset object and its fields
---

# Customer password resets

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

## The customer password reset object

A **customer\_password\_reset** object is returned as part of the response body of each successful [create](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/customer_password_resets/create-customer%20password%20reset.md), [list](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/customer_password_resets/list-all-customer%20password%20resets.md), [retrieve](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/customer_password_resets/retrieve-customer%20password%20reset.md) or [update](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/customer_password_resets/update-customer%20password%20reset.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `customer_password_resets` |
| **id** | `string` | The customer password reset unique identifier |
| links.**self** | `string` | The customer password reset endpoint URL |
| attributes.**customer\_email** | `string` | The email of the customer that requires a password reset |
| attributes.**reset\_password\_token** | `string` | Automatically generated on create. Send its value as the '\_reset\_password\_token' argument when updating the customer password. |
| attributes.**customer\_password** | `string` | The customer new password. This will be accepted only if a valid '\_reset\_password\_token' is sent with the request. |
| attributes.**\_reset\_password\_token** | `string` | Send the 'reset\_password\_token' that you got on create when updating the customer password. |
| attributes.**reset\_password\_at** | `datetime` | Time at which the password was reset. |
| attributes.**id** | `string` | Unique identifier for the resource \(hash\). |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**customer** | `object` | The customer that requires a password reset. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

