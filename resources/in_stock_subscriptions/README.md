---
description: The in stock subscription object and its fields
---

# In stock subscriptions

An "in stock" subscription tracks the customer interest for an SKU that has gone out of stock in a given market. When the SKU returns back in stock, all the active subscriptions receive a 'notify' event and you can attach a webhook to actually notify the customer via email or any other channel.

## The in stock subscription object

An **in stock subscription** object is returned as part of the response body of each successful create, list, retrieve, or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `in_stock_subscriptions` |
| **id** | `string` | The in stock subscription unique identifier |
| links.**self** | `string` | The in stock subscription endpoint URL |
| attributes.**status** | `string` | The subscription status. One of 'active' \(default\), 'inactive', or 'notified' |
| attributes.**customer\_email** | `string` | The email of the associated customer, replace the relationship |
| attributes.**sku\_code** | `string` | The code of the associated sku, replace the relationship |
| attributes.**\_activate** | `boolean, value is 'true'` | Send this attribute if you want to activate an inactive subscription. |
| attributes.**\_deactivate** | `boolean, value is 'true'` | Send this attribute if you want to dactivate an active subscription. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**market** | `object` | The associated market. |
| relationships.**customer** | `object` | The associated customer. |
| relationships.**sku** | `object` | The associated sku. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

