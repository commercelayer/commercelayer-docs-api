---
description: The customer address object and its fields
---

# Customer addresses

Customer addresses are association models that link customers to addresses. Creating a customer address means adding an address to a customer's wallet. During checkout, a logged customer can retrieve their saved addresses and use them as the order shipping or billing addresses.

## The customer address object

A **customer address** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `customer_addresses` |
| **id** | `string` | The customer address unique identifier |
| links.**self** | `string` | The customer address endpoint URL |
| attributes.**name** | `string` | Returns the associated address' name |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**customer** | `object` | The associated customer. |
| relationships.**address** | `object` | The associated address. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

