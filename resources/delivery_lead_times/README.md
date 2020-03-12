---
description: The delivery lead time object and its fields
---

# Delivery lead times

Delivery lead times provide customers with detailed information about their shipments.
This is useful if you ship from many stock locations or offer more shipping method options within a market.


### The delivery lead time object

A **delivery lead time** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/delivery_lead_times/create_delivery_lead_time),
[list](https://docs.commercelayer.io/api/resources/delivery_lead_times/list_delivery_lead_times),
[retrieve](https://docs.commercelayer.io/api/resources/delivery_lead_times/retrieve_delivery_lead_time),
or [update](https://docs.commercelayer.io/api/resources/delivery_lead_times/update_delivery_lead_time) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `delivery_lead_times` |
| **id** | `string` | The delivery lead time unique identifier |
| links.**self** | `string` | The delivery lead time endpoint URL |

| attributes.**min\_hours** | `integer` | The delivery lead minimum time (in hours) when shipping from the associated stock location with the associated shipping method. |

| attributes.**max\_hours** | `integer` | The delivery lead maximun time (in hours) when shipping from the associated stock location with the associated shipping method. |

| attributes.**min\_days** | `integer` | The delivery lead minimum time, in days (rounded) |

| attributes.**max\_days** | `integer` | The delivery lead maximun time, in days (rounded) |

| attributes.**created\_at** | `datetime` | Time at which the resource was created. |

| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |

| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |

| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |

| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**stock\_location** | `object` | The associated stock location. |
| relationships.**shipping\_method** | `object` | The associated shipping method. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

