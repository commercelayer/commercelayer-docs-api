---
description: The paypal payment object and its fields
---

# Paypal payments

PayPal payments can be created and associated with an order in a few steps:

1. Create a Paypal payment, passing a valid return url and cancel url
2. Get the approval url from the response
3. Redirect the customer to the approval url
4. Get the Payer ID from the return url parameters
5. Update the Paypal payment with the Payer ID

PayPal payments are one-time payment sources and cannot be saved in customer wallets.


### The paypal payment object

A **paypal payment** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/paypal_payments/create_paypal_payment),
[list](https://docs.commercelayer.io/api/resources/paypal_payments/list_paypal_payments),
[retrieve](https://docs.commercelayer.io/api/resources/paypal_payments/retrieve_paypal_payment),
or [update](https://docs.commercelayer.io/api/resources/paypal_payments/update_paypal_payment) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `paypal_payments` |
| **id** | `string` | The paypal payment unique identifier |
| links.**self** | `string` | The paypal payment endpoint URL |
| attributes.**return_url** | `string` | The URL where the payer is redirected after they approve the payment. |
| attributes.**cancel_url** | `string` | The URL where the payer is redirected after they cancel the payment. |
| attributes.**note_to_payer** | `string` | A free-form field that you can use to send a note to the payer on PayPal. |
| attributes.**paypal_payer_id** | `string` | The id of the payer that PayPal passes in the return_url. |
| attributes.**name** | `string` | The PayPal payer id (if present) |
| attributes.**paypal_id** | `string` | The id of the PayPal payment object. |
| attributes.**status** | `string` | The PayPal payment status. One of 'created' (default) or 'approved'. |
| attributes.**approval_url** | `string` | The URL the customer should be redirected to approve the payment. |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**order** | `object` | The order associated to the paypal payment, that is set as its payment source. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

