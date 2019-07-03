---
description: The customer subscription object and its fields
---

# Customer subscriptions

Customer subscriptions are simple resources that you can use to track newsletter registrations.
Populate the reference with any key that makes sense to your business domain.
Send the subscriptions to any third party tool or CRM for marketing and segmentation.
Let the customers manage their active subscriptions through their reserved area.


### The customer subscription object

A **customer subscription** object is returned as part of the response body of each successful [create](create-customer subscription.md), [list](list-all-customer subscriptions.md), [retrieve](retrieve-customer subscription.md) or [update](update-customer subscription.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `customer_subscriptions` |
| **id** | `string` | The customer subscription unique identifier |
| links.**self** | `string` | The customer subscription endpoint URL |
| attributes.**customer_email** | `string` | The email of the customer that owns the subscription |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**customer** | `object` | The associated customer. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
