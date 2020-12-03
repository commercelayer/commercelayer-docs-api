---
description: The customer group object and its fields
---

# Customer groups

A customer group is a resource that can be used to organize customers into groups. When you associate a customer group to a market, that market becomes private and can be accessed only by the customers belonging to the group. You can use customer groups to manage B2B customers, B2C loyalty programs, private sales, and more.


### The customer group object

A **customer group** object is returned as part of the response body of each successful create, list, retrieve, or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `customer_groups` |
| **id** | `string` | The customer group unique identifier |
| links.**self** | `string` | The customer group endpoint URL |
| attributes.**name** | `string` | The customer group's internal name |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**customers** | `array` | The customers belonging to this group. |
| relationships.**markets** | `array` | The markets belonging to this group. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

