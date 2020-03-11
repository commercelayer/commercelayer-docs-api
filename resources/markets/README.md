---
description: The market object and its fields
---

# Markets

A market is made of a merchant, an inventory model and a price list (plus an optional geocoder and tax calculator).
Channel applications must specify a market scope when obtaining an access token.
This way, all the resources (e.g., SKUs, prices, stock items) are automatically filtered.


### The market object

A **market** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/markets/create_market),
[list](https://docs.commercelayer.io/api/resources/markets/list_markets),
[retrieve](https://docs.commercelayer.io/api/resources/markets/retrieve_market),
or [update](https://docs.commercelayer.io/api/resources/markets/update_market) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `markets` |
| **id** | `string` | The market unique identifier |
| links.**self** | `string` | The market endpoint URL |

| attributes.**number** | `integer` | Unique identifier for the market (numeric) |

| attributes.**name** | `string` | The market's internal name |

| attributes.**facebook_pixel_id** | `string` | The Facebook Pixed ID |

| attributes.**checkout_url** | `string` | The checkout URL for this market |

| attributes.**private** | `boolean` | Indicates if market belongs to a customer_group. |

| attributes.**created_at** | `datetime` | Time at which the resource was created. |

| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |

| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |

| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |

| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**merchant** | `object` | The associated merchant. |
| relationships.**price_list** | `object` | The associated price list. |
| relationships.**inventory_model** | `object` | The associated inventory model. |
| relationships.**customer_group** | `object` | The associated customer group. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
