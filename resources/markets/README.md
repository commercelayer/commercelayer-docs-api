---
description: The market object and its fields
---

# Markets

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

### The Market object

A market object is returned as part of the response body of each successful [create](create-market.md), [list](list-all-markets.md), [retrieve](retrieve-market.md) or [update](update-market.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `markets` |
| **id** | `string` | The market unique identifier |
| links.**self** | `string` | The market endpoint URL |
| attributes.**number** | `integer` | Unique identified for the market (numeric) |
| attributes.**name** | `string` | The market's internal name |
| attributes.**facebook_pixel_id** | `string` | The Facebook Pixed ID |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**merchant** | `object` | The associated merchant. |
| relationships.**price_list** | `object` | The associated price list. |
| relationships.**inventory_model** | `object` | The associated inventoty model. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
