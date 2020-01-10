---
description: The sku object and its fields
---

# Skus

SKUs describe specific product variations that are being sold.
A unique code identifies each SKU, that can be either the EAN code, the UPC or any other code format.
The SKU name, description and image URL are best suited for internal usage (Commerce Layer is not a CMS).


### The sku object

A **sku** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/skus/create_sku),
[list](https://docs.commercelayer.io/api/resources/skus/list_skus),
[retrieve](https://docs.commercelayer.io/api/resources/skus/retrieve_sku),
or [update](https://docs.commercelayer.io/api/resources/skus/update_sku) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `skus` |
| **id** | `string` | The sku unique identifier |
| links.**self** | `string` | The sku endpoint URL |
| attributes.**code** | `string` | The SKU code, that uniquely identifies the SKU within the organization. |
| attributes.**name** | `string` | The internal name of the . |
| attributes.**description** | `string` | An internal description of the SKU. |
| attributes.**image_url** | `string` | The URL of an image that represents the SKU. |
| attributes.**tag_names** | `string` | A comma separated list of tags. |
| attributes.**pieces_per_pack** | `integer` | The number of pieces that compose the SKU. This is useful to describe sets and bundles. |
| attributes.**weight** | `float` | The weight of the SKU. If present, it will be used to calculate the shipping rates. |
| attributes.**unit_of_weight** | `string` | Can be one of 'gr', or 'oz' |
| attributes.**inventory** | `object` | Aggregated information about the SKU's inventory. Returned only when retrieving a single SKU. |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**shipping_category** | `object` | The SKU's shipping category |
| relationships.**prices** | `array` | The list of prices associated with the SKU. |
| relationships.**stock_items** | `array` | The list of stock items associated with the SKU. |
| relationships.**delivery_lead_times** | `array` | The list of delivery lead times associated with the SKU. |
| relationships.**sku_options** | `array` | The list of SKU options available for the SKU. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
