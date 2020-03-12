---
description: The adyen payment object and its fields
---

# Adyen payments

Adyen payments are a type of payment sources that let you process payments through Adyen — [https://www.adyen.com/](https://www.adyen.com/)


### The adyen payment object

An **adyen payment** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/adyen_payments/create_adyen_payment),
[list](https://docs.commercelayer.io/api/resources/adyen_payments/list_adyen_payments),
[retrieve](https://docs.commercelayer.io/api/resources/adyen_payments/retrieve_adyen_payment),
or [update](https://docs.commercelayer.io/api/resources/adyen_payments/update_adyen_payment) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `adyen_payments` |
| **id** | `string` | The adyen payment unique identifier |
| links.**self** | `string` | The adyen payment endpoint URL |

| attributes.**payment\_methods** | `object` | The merchant available payment methods for the assoiated order (i.e. country and amount). Required by the Adyen JS SDK. |

| attributes.**payment\_request\_data** | `object` | The Adyen payment request data, collected by client. |

| attributes.**payment\_request\_details** | `object` | The Adyen additional details request data, collected by client. |

| attributes.**payment\_response** | `object` | The Adyen payment response, used by client (includes 'resultCode' and 'action'). |

| attributes.**\_authorize** | `boolean, value is 'true'` | Send this attribute if you want to authorize the payment. |

| attributes.**\_details** | `boolean, value is 'true'` | Send this attribute if you want to send additional details the payment request. |

| attributes.**created\_at** | `datetime` | Time at which the resource was created. |

| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |

| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |

| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |

| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**order** | `object` | The order associated to the adyen payment, that is set as its payment source. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

