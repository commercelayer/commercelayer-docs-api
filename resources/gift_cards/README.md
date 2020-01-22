---
description: The gift card object and its fields
---

# Gift cards



### The gift card object

A **gift card** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/gift_cards/create_gift_card),
[list](https://docs.commercelayer.io/api/resources/gift_cards/list_gift_cards),
[retrieve](https://docs.commercelayer.io/api/resources/gift_cards/retrieve_gift_card),
or [update](https://docs.commercelayer.io/api/resources/gift_cards/update_gift_card) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `gift_cards` |
| **id** | `string` | The gift card unique identifier |
| links.**self** | `string` | The gift card endpoint URL |
| attributes.**status** | `string` | The gift card status, one of 'draft', 'inactive', 'active', or 'redeemed'. |
| attributes.**code** | `string` | The gift card code UUID. If not set, it's automatically generated. |
| attributes.**currency_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard. |
| attributes.**initial_balance_cents** | `integer` | The gift card initial balance, in cents. |
| attributes.**initial_balance_float** | `float` | The gift card initial balance, float. |
| attributes.**formatted_initial_balance** | `string` | The gift card initial balance, formatted. |
| attributes.**balance_cents** | `integer` | The gift card balance, in cents. |
| attributes.**balance_float** | `float` | The gift card balance, float. |
| attributes.**formatted_balance** | `string` | The gift card balance, formatted. |
| attributes.**balance_max_cents** | `string` | The gift card balance max, in cents. |
| attributes.**balance_max_float** | `float` | The gift card balance max, float. |
| attributes.**formatted_balance_max** | `string` | The gift card balance max, formatted. |
| attributes.**balance_log** | `object` | The gift card balance log. Tracks all the gift card transactions. |
| attributes.**single_use** | `boolean` | Indicates if the gift card can be used only one. |
| attributes.**rechargeable** | `boolean` | Indicates if the gift card can be recharged. |
| attributes.**image_url** | `string` | The URL of an image that represents the gift card. |
| attributes.**expires_at** | `datetime` | Time at which the gift card will expire. |
| attributes.**reference_origin** | `string` | A string that you can use to specify the origin of the resource reference. This can be useful for integrating this resource type to more external systems. |
| attributes.**recipient_email** | `string` | The email address of the associated recipient. When creating or updating a gift card, this is a shortcut to find or create the associated recipient by email. |
| attributes.**_purchase** | `boolean, value is 'true'` | Send this attribute if you want to confirm a draft gift card. The gift card becomes 'inactive', waiting to be activated. |
| attributes.**_activate** | `boolean, value is 'true'` | Send this attribute if you want to activate a gift card. |
| attributes.**_deactivate** | `boolean, value is 'true'` | Send this attribute if you want to deactivate a gift card. |
| attributes.**_balance_change_cents** | `integer` | The balance change, in cents. Send a negative value to reduces the card balance by the specified amount. Send a positive value to recharge the gift card (if rechargeable). |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**market** | `object` | The associated market (optional). |
| relationships.**gift_card_recipient** | `object` | The associated gift card recipient (optional). |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
