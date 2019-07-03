---
description: The shipping category object and its fields
---

# Shipping categories

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

### The shipping category object

A **shipping category** object is returned as part of the response body of each successful [create](create-shipping category.md), [list](list-all-shipping categories.md), [retrieve](retrieve-shipping category.md) or [update](update-shipping category.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `shipping_categories` |
| **id** | `string` | The shipping category unique identifier |
| links.**self** | `string` | The shipping category endpoint URL |
| attributes.**name** | `string` | The shipping category name. |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**skus** | `array` | The associated skus. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
