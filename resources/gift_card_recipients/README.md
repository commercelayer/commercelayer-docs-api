---
description: The gift card recipient object and its fields
---

# Gift card recipients



### The gift card recipient object

A **gift card recipient** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/gift_card_recipients/create_gift_card_recipient),
[list](https://docs.commercelayer.io/api/resources/gift_card_recipients/list_gift_card_recipients),
[retrieve](https://docs.commercelayer.io/api/resources/gift_card_recipients/retrieve_gift_card_recipient),
or [update](https://docs.commercelayer.io/api/resources/gift_card_recipients/update_gift_card_recipient) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `gift_card_recipients` |
| **id** | `string` | The gift card recipient unique identifier |
| links.**self** | `string` | The gift card recipient endpoint URL |
| attributes.**email** | `string` | The gift card recipient email address |
| attributes.**first_name** | `string` | The gift card recipient first name |
| attributes.**last_name** | `string` | The gift card recipient last name |
| attributes.**reference_origin** | `string` | A string that you can use to specify the origin of the resource reference. This can be useful for integrating this resource type to more external systems. |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**customer** | `object` | The associated customer. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
