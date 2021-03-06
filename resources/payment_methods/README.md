---
description: The payment method object and its fields
---

# Payment methods

Payment methods represent the type of payment sources (e.g., Credit Card, PayPal, or Apple Pay) offered in a market. They can have a price and must be present before placing an order.


### The payment method object

A **payment method** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `payment_methods` |
| **id** | `string` | The payment method unique identifier |
| links.**self** | `string` | The payment method endpoint URL |
| attributes.**payment_source_type** | `string` | The payment source type, can be one of: 'AdyenPayment', 'BraintreePayment', 'CheckoutComPayment', 'CreditCard', 'ExternalPayment', 'PaypalPayment', 'StripePayment', or 'WireTransfer'. |
| attributes.**name** | `string` | Payment source type, titleized |
| attributes.**disabled_at** | `datetime` | Time at which the payment method was disabled. |
| attributes.**price_amount_cents** | `integer` | The payment method's price, in cents |
| attributes.**price_amount_float** | `float` | The payment method's price, float |
| attributes.**formatted_price_amount** | `string` | The payment method's price, formatted |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**market** | `object` | The associated market. |
| relationships.**payment_gateway** | `object` | The associated payment gateway. |
| relationships.**attachments** | `array` | The associated attachments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

