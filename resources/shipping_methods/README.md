---
description: The shipping method object and its fields
---

# Shipping methods

Shipping methods are used to provide customers with more delivery options.
Each shipping method can have a price and can be free over a specific order's amount.


### The shipping method object

A **shipping method** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/shipping_methods/create_shipping_method),
[list](https://docs.commercelayer.io/api/resources/shipping_methods/list_shipping_methods),
[retrieve](https://docs.commercelayer.io/api/resources/shipping_methods/retrieve_shipping_method),
or [update](https://docs.commercelayer.io/api/resources/shipping_methods/update_shipping_method) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `shipping_methods` |
| **id** | `string` | The shipping method unique identifier |
| links.**self** | `string` | The shipping method endpoint URL |

| attributes.**name** | `string` | The shipping method's name |

| attributes.**disabled\_at** | `datetime` | Time at which the shipping method was disabled. |

| attributes.**currency\_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard, automatically inherited from the associated market. |

| attributes.**price\_amount\_cents** | `integer` | The price of this shipping method, in cents. |

| attributes.**price\_amount\_float** | `float` | The price of this shipping method, float. |

| attributes.**formatted\_price\_amount** | `string` | The price of this shipping method, formatted. |

| attributes.**free\_over\_amount\_cents** | `integer` | Apply free shipping if the order amount is over this value, in cents. |

| attributes.**free\_over\_amount\_float** | `float` | Apply free shipping if the order amount is over this value, float. |

| attributes.**formatted\_free\_over\_amount** | `string` | Apply free shipping if the order amount is over this value, formatted. |

| attributes.**price\_amount\_for\_shipment\_cents** | `integer` | The calculated price (zero or price amount) when associated to a shipment, in cents. |

| attributes.**price\_amount\_for\_shipment\_float** | `float` | The calculated price (zero or price amount) when associated to a shipment, float. |

| attributes.**formatted\_price\_amount\_for\_shipment** | `string` | The calculated price (zero or price amount) when associated to a shipment, formatted. |

| attributes.**created\_at** | `datetime` | Time at which the resource was created. |

| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |

| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |

| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |

| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**market** | `object` | The market where this shipping method is available. |
| relationships.**shipping\_zone** | `object` | The shipping zone that is used to match the order shipping address. |
| relationships.**shipping\_category** | `object` | The shipping category for which this shipping method is available. |
| relationships.**delivery\_lead\_time\_for\_shipment** | `object` | The delivery lead time for the associated shipment. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

