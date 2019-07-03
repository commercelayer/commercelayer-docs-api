---
description: The payment method object and its fields
---

# Payment methods

Payment methods represent the type of payment sources (e.g., Credit Card, PayPal or Apple Pay) offered in a market.
They can have a price and must be present before placing an order ([learn more](https://commercelayer.io/glossary/payment_method/)).


### The payment method object

A **payment method** object is returned as part of the response body of each successful [create](create-payment method.md), [list](list-all-payment methods.md), [retrieve](retrieve-payment method.md) or [update](update-payment method.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `payment_methods` |
| **id** | `string` | The payment method unique identifier |
| links.**self** | `string` | The payment method endpoint URL |
| attributes.**payment_source_type** | `string` | Can be one of 'PaypalPayment', or 'CreditCard' |
| attributes.**name** | `string` | Payment source type, titleized |
| attributes.**disabled_at** | `datetime` | Time at which the payment method was disabled. |
| attributes.**price_amount_cents** | `integer` | The payment method's price, in cents |
| attributes.**price_amount_float** | `float` | The payment method's price, number |
| attributes.**formatted_price_amount** | `string` | The payment method's price, formatted |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**market** | `object` | The associated market. |
| relationships.**payment_gateway** | `object` | The associated payment gateway. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
