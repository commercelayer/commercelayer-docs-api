---
description: The customer subscription object and its fields
---

# Customer subscriptions

Customer subscriptions are simple resources that you can use to track newsletter registrations.
Populate the reference with any key that makes sense to your business domain.
Send the subscriptions to any third party tool or CRM for marketing and segmentation.
Let the customers manage their active subscriptions through their reserved area.


### The customer subscription object

A **customer subscription** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/customer_subscriptions/create_customer_subscription),
[list](https://docs.commercelayer.io/api/resources/customer_subscriptions/list_customer_subscriptions),
[retrieve](https://docs.commercelayer.io/api/resources/customer_subscriptions/retrieve_customer_subscription),
or [update](https://docs.commercelayer.io/api/resources/customer_subscriptions/update_customer_subscription) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `customer_subscriptions` |
| **id** | `string` | The customer subscription unique identifier |
| links.**self** | `string` | The customer subscription endpoint URL |

| attributes.**customer_email** | `string` | The email of the customer that owns the subscription |

| attributes.**created_at** | `datetime` | Time at which the resource was created. |

| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |

| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |

| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |

| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**customer** | `object` | The associated customer. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
