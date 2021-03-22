---
description: The stripe gateway object and its fields
---

# Stripe gateways

Connect the Stripe payment gateway in order to be able to safely process payments through Stripe — [https://stripe.com/](https://stripe.com/)

## The stripe gateway object

A **stripe gateway** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `stripe_gateways` |
| **id** | `string` | The stripe gateway unique identifier |
| links.**self** | `string` | The stripe gateway endpoint URL |
| attributes.**name** | `string` | The payment gateway's internal name. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| attributes.**login** | `string` | The gateway login. |
| attributes.**webhook\_endpoint\_id** | `string` | The gateway webhook endpoint ID, generated automatically. |
| attributes.**webhook\_endpoint\_secret** | `string` | The gateway webhook endpoint secret, generated automatically. |
| attributes.**webhook\_endpoint\_url** | `string` | The gateway webhook URL, generated automatically. |
| relationships.**payment\_methods** | `array` | The associated payment methods. |
| relationships.**stripe\_payments** | `array` | The associated payments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

