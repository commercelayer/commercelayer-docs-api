---
description: The checkout com payment object and its fields
---

# Checkout com payments

Checkout.com payments are a type of payment sources that let you process payments through Checkout.com — [https://www.checkout.com/](https://www.checkout.com/)


### The checkout com payment object

A **checkout com payment** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `checkout_com_payments` |
| **id** | `string` | The checkout com payment unique identifier |
| links.**self** | `string` | The checkout com payment endpoint URL |
| attributes.**payment_type** | `string` | The payment source type. |
| attributes.**token** | `string` | The Checkout.com card or digital wallet token. |
| attributes.**session_id** | `string` | A payment session ID used to obtain the details. |
| attributes.**source_id** | `string` | The payment source identifier that can be used for subsequent payments. |
| attributes.**customer_token** | `string` | The customer's unique identifier. This can be passed as a source when making a payment. |
| attributes.**redirect_uri** | `string` | The URI that the customer should be redirected to in order to complete the payment. |
| attributes.**payment_response** | `object` | The Checkout.com payment response, used to fetch internal data. |
| attributes.**_authorize** | `boolean, value is 'true'` | Send this attribute if you want to authorize the payment. |
| attributes.**_details** | `boolean, value is 'true'` | Send this attribute if you want to send additional details the payment request (i.e. upon 3DS check). |
| attributes.**_refresh** | `boolean, value is 'true'` | Send this attribute if you want to refresh all the pending transactions, can be used as webhooks fallback logic. |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**order** | `object` | The order associated to the Checkout.com payment, that is set as its payment source. |
| relationships.**payment_gateway** | `object` | The associated payment gateway, inherited by the order payment_method. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

