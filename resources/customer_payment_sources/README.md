---
description: The customer payment source object and its fields
---

# Customer payment sources

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

### The customer payment source object

A **customer_payment_source** object is returned as part of the response body of each successful [create](create-customer payment source.md), [list](list-all-customer payment sources.md), [retrieve](retrieve-customer payment source.md) or [update](update-customer payment source.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `customer_payment_sources` |
| **id** | `string` | The customer payment source unique identifier |
| links.**self** | `string` | The customer payment source endpoint URL |
| attributes.**name** | `string` | Returns the associated payment source's name |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**customer** | `object` | The associated customer. |
| relationships.**payment_source** | `object` | The associated payment source (i.e. credit card). |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
