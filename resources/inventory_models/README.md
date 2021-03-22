---
description: The inventory model object and its fields
---

# Inventory models

An inventory model defines a list of stock locations ordered by priority. The priority and cutoff determine how the availability of SKUs gets calculated within a market. If an order contains line items from two or more stock locations, the order is split into two or more shipments, one for each location.

## The inventory model object

An **inventory model** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `inventory_models` |
| **id** | `string` | The inventory model unique identifier |
| links.**self** | `string` | The inventory model endpoint URL |
| attributes.**name** | `string` | The inventory model's internal name. |
| attributes.**strategy** | `string` | The inventory model's shipping strategy: one between 'split\_shipments' \(default\), 'ship\_from\_primary', 'ship\_from\_first\_available\_or\_primary' and 'ship\_from\_most\_available'. |
| attributes.**stock\_locations\_cutoff** | `integer` | The maximum number of stock locations used for inventory computation |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**inventory\_stock\_locations** | `array` | The resources that assign a priority to each inventory model stock location. |
| relationships.**inventory\_return\_locations** | `array` | The resources that assign a priority to each inventory model return location. |
| relationships.**attachments** | `array` | The associated attachments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

