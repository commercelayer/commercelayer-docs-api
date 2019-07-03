---
description: The merchant object and its fields
---

# Merchants

A merchant is the fiscal representative that is selling in a specific market.
Tax calculators use the merchant's address (and the shipping address) to determine the tax rate for an order ([learn more](https://commercelayer.io/glossary/merchant/)).


### The merchant object

A **merchant** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/resources/merchants/create_merchant),
[list](https://docs.commercelayer.io/resources/merchants/list_merchants),
[retrieve](https://docs.commercelayer.io/resources/merchants/retrieve_merchant),
or [update](https://docs.commercelayer.io/resources/merchants/update_merchant) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `merchants` |
| **id** | `string` | The merchant unique identifier |
| links.**self** | `string` | The merchant endpoint URL |
| attributes.**name** | `string` | The merchant's internal name |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**address** | `object` | The associated address. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
