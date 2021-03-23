---
description: The payment gateway object and its fields
---

# Payment gateways



### The payment gateway object

A **payment gateway** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `payment_gateways` |
| **id** | `string` | The payment gateway unique identifier |
| links.**self** | `string` | The payment gateway endpoint URL |
| attributes.**name** | `string` | The payment gateway's internal name. |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**payment_methods** | `array` | The associated payment methods. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

