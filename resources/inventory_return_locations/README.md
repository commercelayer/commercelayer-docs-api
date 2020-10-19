---
description: The inventory return location object and its fields
---

# Inventory return locations

Inventory return location build a hierarchy of stock locations within an inventory model.
In case an SKU is available in more stock locations, it gets returned to those with the highest priority.


### The inventory return location object

An **inventory return location** object is returned as part of the response body of each successful create, list, retrieve, or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `inventory_return_locations` |
| **id** | `string` | The inventory return location unique identifier |
| links.**self** | `string` | The inventory return location endpoint URL |
| attributes.**priority** | `integer` | The inventory return location priority within the associated invetory model. |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**stock_location** | `object` | The associated return location. |
| relationships.**inventory_model** | `object` | The associated inventory model. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

