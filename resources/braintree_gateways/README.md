---
description: The braintree gateway object and its fields
---

# Braintree gateways

Connect the Braintree payment gateway in order to be able to safely process payments through Braintree — [https://www.braintreepayments.com/](https://www.braintreepayments.com/)


### The braintree gateway object

A **braintree gateway** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `braintree_gateways` |
| **id** | `string` | The braintree gateway unique identifier |
| links.**self** | `string` | The braintree gateway endpoint URL |
| attributes.**name** | `string` | The payment gateway's internal name. |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| attributes.**merchant_account_id** | `string` | The gateway merchant account ID. |
| attributes.**merchant_id** | `string` | The gateway merchant ID. |
| attributes.**public_key** | `string` | The gateway API public key. |
| attributes.**private_key** | `string` | The gateway API private key. |
| attributes.**descriptor_name** | `string` | The dynamic descriptor name. Must be composed by business name (3, 7 or 12 chars), an asterisk (*) and the product name (18, 14 or 9 chars), for a total length of 22 chars. |
| attributes.**descriptor_phone** | `string` | The dynamic descriptor phone number. |
| attributes.**descriptor_url** | `string` | The dynamic descriptor URL. |
| attributes.**webhook_endpoint_url** | `string` | The gateway webhook URL, generated automatically. |
| relationships.**payment_methods** | `array` | The associated payment methods. |
| relationships.**braintree_payments** | `array` | The associated payments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

