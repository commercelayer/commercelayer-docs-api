---
description: The stock item object and its fields
---

# Stock items

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

### The Stock item object

A stock item object is returned as part of the response body of each successful [create](create-stock item.md), [list](list-all-stock items.md), [retrieve](retrieve-stock item.md) or [update](update-stock item.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `stock items` |
| **id** | `string` | The stock item unique identifier |
| links.**self** | `string` | The stock item endpoint URL |
| attributes.**sku_code** | `string` | The code of the associated sku. |
| attributes.**quantity** | `integer` | The stock item quantity. |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**stock_location** | `object` | The associated stock location. |
| relationships.**sku** | `object` | The associated stock sku. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
