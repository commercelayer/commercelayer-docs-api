---
description: The payment method object and its fields
---

# Payment methods

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

### The Payment method object

A payment method object is returned as part of the response body of each successful [create](create-payment method.md), [list](list-all-payment methods.md), [retrieve](retrieve-payment method.md) or [update](update-payment method.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `payment methods` |
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
| relationships.**market** | `has_one` | The associated market. |
| relationships.**payment_gateway** | `has_one` | The associated payment gateway. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
