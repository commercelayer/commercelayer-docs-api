---
description: The braintree payment object and its fields
---

# Braintree payments

Braintree payments are a type of payment sources that let you process payments through Braintree — [https://www.braintreepayments.com/](https://www.braintreepayments.com/)


### The braintree payment object

A **braintree payment** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `braintree_payments` |
| **id** | `string` | The braintree payment unique identifier |
| links.**self** | `string` | The braintree payment endpoint URL |
| attributes.**client_token** | `string` | The Braintree payment client token. Required by the Braintree JS SDK. |
| attributes.**payment_method_nonce** | `string` | The Braintree payment method nonce. Sent by the Braintree JS SDK. |
| attributes.**payment_id** | `string` | The Braintree payment ID used by local payment and sent by the Braintree JS SDK. |
| attributes.**local** | `boolean` | Indicates if the payment is local, in such case Braintree will trigger a webhook call passing the "payment_id" and "payment_method_nonce" in order to complete the transaction. |
| attributes.**options** | `object` | Braintree payment options: 'customer_id' and 'payment_method_token' |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**order** | `object` | The order associated to the braintree payment, that is set as its payment source. |
| relationships.**payment_gateway** | `object` | The associated payment gateway, inherited by the order payment_method. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

