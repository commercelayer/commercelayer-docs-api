---
description: The SKU object and its fields
---

# SKUs

SKUs describe specific product variations that are being sold. 

A unique code identifies each SKU, that can be either the [EAN](https://en.wikipedia.org/wiki/International_Article_Number) code, the [UPC](https://en.wikipedia.org/wiki/Universal_Product_Code) or any other code format. 

{% hint style="info" %}
The SKU name, description and image URL are best suited for internal usage — **Commerce Layer is not a CMS**.
{% endhint %}

### The SKU object

An SKU object is returned as part of the response body of each successful [create](create-an-sku.md), [list](list-all-the-skus.md), [retrieve](retrieve-a-sku.md) or [update](update-a-sku.md) API call. 

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `skus` |
| **id** | `string` | The SKU unique identifier |
| links.**self** | `string` | The SKU endpoint URL |
| attributes.**code** | `string` | The SKU code, that uniquely identifies the SKU within the organization |
| attributes.**name** | `string` | The internal name of the SKU |
| attributes.**description** | `string` | An internal description of the SKU |
| attributes.**image\_url** | `string` | The URL of an image that represents the SKU |
| attributes.**tag\_names** | `string` | A comma-separated list of tags |
| attributes.**pieces\_per\_pack** | `integer` | The number of pieces that compose the SKU \(this is useful to describe sets and bundles\) |
| attributes.**weight** | `float` | The weight of the SKU \(if present, it will be used to calculate the shipping rates\) |
| attributes.**unit\_of\_weight** | `string` | Can be one of `gr` or `oz` |
| attributes.**inventory** | `object` | Some aggregated information about the SKU's inventory \(returned only when retrieving a single SKU with a **channel** application\) |
| attributes.**id** | `integer` | The unique identifier for the SKU |
| attributes.**created\_at** | `datetime` | Time at which the SKU was created |
| attributes.**updated\_at** | `datetime` | Time at which the SKU was last updated |
| attributes.**reference** | `string` | Your own identifier to the SKU \(this can be useful for integrating the SKU to an external system, like an ERP, a marketing tool or a CRM\) |
| attributes.**metadata** | `object` | A set of key-value pairs that you can attach to the SKU \(this can be useful for storing additional information about the SKU in a structured format\) |
| relationships.**shipping\_category** | `object` | The SKU shipping category |
| relationships.**prices** | `array` | The list of prices associated with the SKU |
| relationships.**stock\_items** | `array` | The list of stock items associated with the SKU |
| realtionships.**delivery\_lead\_times** | `array` | The list of delivery lead times associated with the SKU |
| relationships.**sku\_options** | `array` | The list of SKU options available for the SKU |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

