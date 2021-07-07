---
description: The bundle object and its fields
---

# Bundles

Bundles describe a set of specific products that are being sold. A unique code identifies each bundle within the market. The bundle name, description, and image URL are best suited for internal usage \(Commerce Layer is not a CMS\). Bundles are linked to manual SKU lists, inheriting the SKUs from there. A **maximum of 5 SKU list items** are permitted for each bundle.  
Once an SKU list is associated with a bundle, its items cannot be added, removed or updated, unless you first destroy all of the linked bundles. Bundles have `price_amount_cents` and `compare_at_amount_cents` attributes: the latter can be specified or computed as the sum the SKUs, but is always guaranteed to be smaller or equal than the former.

## The bundle object

A **bundle** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `bundles` |
| **id** | `string` | The bundle unique identifier |
| links.**self** | `string` | The bundle endpoint URL |
| attributes.**code** | `string` | The bundle code, that uniquely identifies the bundle within the market. |
| attributes.**name** | `string` | The internal name of the bundle. |
| attributes.**description** | `string` | An internal description of the bundle. |
| attributes.**image\_url** | `string` | The URL of an image that represents the bundle. |
| attributes.**price\_amount\_cents** | `integer` | The bundle price amount for the associated market, in cents. |
| attributes.**price\_amount\_float** | `float` | The bundle price amount for the associated market, float. |
| attributes.**formatted\_price\_amount** | `string` | The bundle price amount for the associated market, formatted. |
| attributes.**compare\_at\_amount\_cents** | `integer` | The compared price amount, in cents. Useful to display a percentage discount. |
| attributes.**compare\_at\_amount\_float** | `float` | The compared price amount, float. |
| attributes.**formatted\_compare\_at\_amount** | `string` | The compared price amount, formatted. |
| attributes.**\_compute\_compare\_at\_amount** | `boolean, value is 'true'` | Send this attribute if you want to compute the compare\_at\_amount\_cents as the sum of the prices of the bundle SKUs for the market. |
| attributes.**skus\_count** | `integer` | The total number of SKUs in the bundle. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**market** | `object` | The associated market. |
| relationships.**sku\_list** | `object` | The associated SKU list. |
| relationships.**skus** | `array` | The associated SKUs. |
| relationships.**attachments** | `array` | The associated attachments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

