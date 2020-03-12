---
description: The SKU option object and its fields
---

# Sku options

SKU options represent any personalization or feature that customers can add to selected SKUs.
They can have a price and a delay time (e.g., preparation time) and are defined by market.


### The SKU option object

A **SKU option** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/sku_options/create_sku_option),
[list](https://docs.commercelayer.io/api/resources/sku_options/list_sku_options),
[retrieve](https://docs.commercelayer.io/api/resources/sku_options/retrieve_sku_option),
or [update](https://docs.commercelayer.io/api/resources/sku_options/update_sku_option) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `sku_options` |
| **id** | `string` | The SKU option unique identifier |
| links.**self** | `string` | The SKU option endpoint URL |

| attributes.**name** | `string` | The marsku option's internal name |

| attributes.**description** | `string` | An internal description of the sku option. |

| attributes.**price_amount_cents** | `integer` | The price of this shipping method, in cents. |

| attributes.**price_amount_float** | `float` | The price of this shipping method, float. |

| attributes.**formatted_price_amount** | `string` | The price of this shipping method, formatted. |

| attributes.**delay_hours** | `integer` | The delay time (in hours) that should be added to the delivery lead time when this option is purchased. |

| attributes.**delay_days** | `integer` | The delay time, in days (rounded) |

| attributes.**sku_code_regex** | `string` | The regex that will be evaluated to match the sku codes. |

| attributes.**created_at** | `datetime` | Time at which the resource was created. |

| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |

| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |

| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |

| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**market** | `object` | The associated market. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

