---
description: The customer group object and its fields
---

# Customer groups

A customer group is a resource that can be used to organize customers into groups.
When you associate a price list to a customer group, all the customers belonging to that group get its price list, overridining the one defined at market level.
You can use customer groups to manage B2B customers, B2C loyalty programs, and more.


### The customer group object

A **customer group** object is returned as part of the response body of each successful [create](create-customer group.md), [list](list-all-customer groups.md), [retrieve](retrieve-customer group.md) or [update](update-customer group.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `customer_groups` |
| **id** | `string` | The customer group unique identifier |
| links.**self** | `string` | The customer group endpoint URL |
| attributes.**name** | `string` | The customer group's internal name |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**price_list** | `object` | The associated price list. |
| relationships.**customers** | `array` | The customers belonging to this group. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
