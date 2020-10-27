---
description: The market object and its fields
---

# Markets

A market is made of a merchant, an inventory model, and a price list \(plus an optional customer group, geocoder, and tax calculator\). Sales channel applications must specify a market scope when obtaining an access token. This way, all the resources \(e.g., SKUs, prices, stock items\) are automatically filtered.

## The market object

A **market** object is returned as part of the response body of each successful create, list, retrieve, or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `markets` |
| **id** | `string` | The market unique identifier |
| links.**self** | `string` | The market endpoint URL |
| attributes.**number** | `integer` | Unique identifier for the market \(numeric\) |
| attributes.**name** | `string` | The market's internal name |
| attributes.**facebook\_pixel\_id** | `string` | The Facebook Pixed ID |
| attributes.**checkout\_url** | `string` | The checkout URL for this market |
| attributes.**external\_prices\_url** | `string` | The URL used to fetch prices from an external source |
| attributes.**private** | `boolean` | Indicates if market belongs to a customer\_group. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**merchant** | `object` | The associated merchant. |
| relationships.**price\_list** | `object` | The associated price list. |
| relationships.**inventory\_model** | `object` | The associated inventory model. |
| relationships.**customer\_group** | `object` | The associated customer group. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

