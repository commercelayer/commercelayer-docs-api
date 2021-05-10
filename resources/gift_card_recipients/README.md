---
description: The gift card recipient object and its fields
---

# Gift card recipients

When purchasing a gift card, you might want to send it to a recipient, either via email or physically — e.g. by printing the gift card and shipping it to a friend. To do that, you can create a gift card recipient and associate it with the purchased gift card. When the gift card is redeemed, you can then associate the gift card recipient with the customer that placed the order, so that the gift card is linked to their personal information.


### The gift card recipient object

A **gift card recipient** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `gift_card_recipients` |
| **id** | `string` | The gift card recipient unique identifier |
| links.**self** | `string` | The gift card recipient endpoint URL |
| attributes.**email** | `string` | The gift card recipient email address |
| attributes.**first_name** | `string` | The gift card recipient first name |
| attributes.**last_name** | `string` | The gift card recipient last name |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**customer** | `object` | The associated customer. |
| relationships.**attachments** | `array` | The associated attachments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

