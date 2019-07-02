---
description: The customer subscription object and its fields
---

# Customer subscriptions

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

### The Customer subscription object

A customer subscription object is returned as part of the response body of each successful [create](create-customer subscription.md), [list](list-all-customer subscriptions.md), [retrieve](retrieve-customer subscription.md) or [update](update-customer subscription.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `customer subscriptions` |
| **id** | `string` | The customer subscription unique identifier |
| links.**self** | `string` | The customer subscription endpoint URL |
| attributes.**customer_email** | `string` | The email of the customer that owns the subscription |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**customer** | `has_one` | The associated customer. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
