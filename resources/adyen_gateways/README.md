---
description: The adyen gateway object and its fields
---

# Adyen gateways

Connect the Adyen payment gateway in order to be able to safely process payments through Adyen — [https://www.adyen.com/](https://www.adyen.com/)


### The adyen gateway object

An **adyen gateway** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `adyen_gateways` |
| **id** | `string` | The adyen gateway unique identifier |
| links.**self** | `string` | The adyen gateway endpoint URL |
| attributes.**name** | `string` | The payment gateway's internal name. |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| attributes.**merchant_account** | `string` | The gateway merchant account. |
| attributes.**api_key** | `string` | The gateway API key. |
| attributes.**live_url_prefix** | `string` | The prefix of the endpoint used for live transactions. |
| relationships.**payment_methods** | `array` | The associated payment methods. |
| relationships.**adyen_payments** | `array` | The associated payments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

