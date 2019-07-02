---
description: The sku option object and its fields
---

# Sku options

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

### The Sku option object

A sku option object is returned as part of the response body of each successful [create](create-sku option.md), [list](list-all-sku options.md), [retrieve](retrieve-sku option.md) or [update](update-sku option.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `sku options` |
| **id** | `string` | The sku option unique identifier |
| links.**self** | `string` | The sku option endpoint URL |
| attributes.**name** | `string` | The marsku option's internal name |
| attributes.**description** | `string` | An internal description of the sku option. |
| attributes.**price_amount_cents** | `integer` | The price of this shipping method, in cents. |
| attributes.**price_amount_float** | `float` | The price of this shipping method, float. |
| attributes.**formatted_price_amount** | `string` | The price of this shipping method, formatted. |
| attributes.**delay_hours** | `integer` | The delay time (in hours) that should be added to the delivery lead time when this option is purchased. |
| attributes.**delay_days** | `integer` | The delay time, in days (rounded) |
| attributes.**sku_code_regex** | `string` | The regex that will be evaluated to match the sku codes. |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**market** | `has_one` | The associated market. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |