---
description: The stripe payment object and its fields
---

# Stripe payments

Stripe payments are a type of payment sources that let you process payments through Stripe — [https://stripe.com/](https://stripe.com/)


### The stripe payment object

A **stripe payment** object is returned as part of the response body of each successful create, list, retrieve, or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `stripe_payments` |
| **id** | `string` | The stripe payment unique identifier |
| links.**self** | `string` | The stripe payment endpoint URL |
| attributes.**client_secret** | `string` | The Stripe payment intent client secret. Required to create a charge through Stripe.js. |
| attributes.**options** | `object` | Stripe payment options: 'setup_future_usage', 'customer', and 'payment_method' |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**order** | `object` | The order associated to the stripe payment, that is set as its payment source. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

