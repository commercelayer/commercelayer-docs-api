---
description: The payment method object and its fields
---

# Payment methods

Payment methods represent the type of payment sources (e.g., Credit Card, PayPal or Apple Pay) offered in a market.
They can have a price and must be present before placing an order.


### The payment method object

A **payment method** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/payment_methods/create_payment_method),
[list](https://docs.commercelayer.io/api/resources/payment_methods/list_payment_methods),
[retrieve](https://docs.commercelayer.io/api/resources/payment_methods/retrieve_payment_method),
or [update](https://docs.commercelayer.io/api/resources/payment_methods/update_payment_method) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `payment_methods` |
| **id** | `string` | The payment method unique identifier |
| links.**self** | `string` | The payment method endpoint URL |

| attributes.**payment\_source\_type** | `string` | Can be one of 'PaypalPayment', or 'CreditCard' |

| attributes.**name** | `string` | Payment source type, titleized |

| attributes.**disabled\_at** | `datetime` | Time at which the payment method was disabled. |

| attributes.**price\_amount\_cents** | `integer` | The payment method's price, in cents |

| attributes.**price\_amount\_float** | `float` | The payment method's price, number |

| attributes.**formatted\_price\_amount** | `string` | The payment method's price, formatted |

| attributes.**created\_at** | `datetime` | Time at which the resource was created. |

| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |

| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |

| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |

| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**market** | `object` | The associated market. |
| relationships.**payment\_gateway** | `object` | The associated payment gateway. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

