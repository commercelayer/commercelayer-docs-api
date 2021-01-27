---
description: The paypal payment object and its fields
---

# Paypal payments

PayPal payments can be created and associated with an order in a few steps:

1. Create a Paypal payment, passing a valid `return_url` and `cancel_url`
2. Get the `approval_url` from the response
3. Redirect the customer to the approval URL
4. Get the `paypal_payer_id` from the return url parameters
5. Update the PayPal payment with the payer ID

PayPal payments are one-time payment sources and cannot be saved in customer wallets.

## The paypal payment object

A **paypal payment** object is returned as part of the response body of each successful create, list, retrieve, or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `paypal_payments` |
| **id** | `string` | The paypal payment unique identifier |
| links.**self** | `string` | The paypal payment endpoint URL |
| attributes.**return\_url** | `string` | The URL where the payer is redirected after they approve the payment. |
| attributes.**cancel\_url** | `string` | The URL where the payer is redirected after they cancel the payment. |
| attributes.**note\_to\_payer** | `string` | A free-form field that you can use to send a note to the payer on PayPal. |
| attributes.**paypal\_payer\_id** | `string` | The id of the payer that PayPal passes in the return\_url. |
| attributes.**name** | `string` | The PayPal payer id \(if present\) |
| attributes.**paypal\_id** | `string` | The id of the PayPal payment object. |
| attributes.**status** | `string` | The PayPal payment status. One of 'created' \(default\) or 'approved'. |
| attributes.**approval\_url** | `string` | The URL the customer should be redirected to approve the payment. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**order** | `object` | The order associated to the paypal payment, that is set as its payment source. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

