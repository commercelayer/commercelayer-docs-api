---
description: The paypal payment object and its fields
---

# Paypal payments

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

### The paypal payment object

A **paypal_payment** object is returned as part of the response body of each successful [create](create-paypal payment.md), [list](list-all-paypal payments.md), [retrieve](retrieve-paypal payment.md) or [update](update-paypal payment.md) API call.

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
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**order** | `object` | The order associated to the paypal payment, that is set as its payment source. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
