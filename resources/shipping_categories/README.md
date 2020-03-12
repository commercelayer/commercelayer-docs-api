---
description: The shipping category object and its fields
---

# Shipping categories

Shipping categories determine which shipping methods are available for the associated SKUs.
An order is split into more shipments if it contains line items belonging to more than one shipping category.


### The shipping category object

A **shipping category** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/shipping_categories/create_shipping_category),
[list](https://docs.commercelayer.io/api/resources/shipping_categories/list_shipping_categories),
[retrieve](https://docs.commercelayer.io/api/resources/shipping_categories/retrieve_shipping_category),
or [update](https://docs.commercelayer.io/api/resources/shipping_categories/update_shipping_category) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `shipping_categories` |
| **id** | `string` | The shipping category unique identifier |
| links.**self** | `string` | The shipping category endpoint URL |
| attributes.**name** | `string` | The shipping category name. |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**skus** | `array` | The associated skus. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

