---
description: The gift card object and its fields
---

# Gift cards

A gift card is a special type of payment instrument that can be either purchased or used to pay for an order — in total or in part — depending on its outstanding balance. All gift cards must be activated before being used. Rechargeable gift cards can be reloaded at any time. Single-use gift cards become redeemed after the first usage, whatever the balance used. Associate a gift card to a market if you want to restrict its availability to that specific market.

## The gift card object

A **gift card** object is returned as part of the response body of each successful create, list, retrieve, or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `gift_cards` |
| **id** | `string` | The gift card unique identifier |
| links.**self** | `string` | The gift card endpoint URL |
| attributes.**status** | `string` | The gift card status, one of 'draft', 'inactive', 'active', or 'redeemed'. |
| attributes.**code** | `string` | The gift card code UUID. If not set, it's automatically generated. |
| attributes.**currency\_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard. |
| attributes.**initial\_balance\_cents** | `integer` | The gift card initial balance, in cents. |
| attributes.**initial\_balance\_float** | `float` | The gift card initial balance, float. |
| attributes.**formatted\_initial\_balance** | `string` | The gift card initial balance, formatted. |
| attributes.**balance\_cents** | `integer` | The gift card balance, in cents. |
| attributes.**balance\_float** | `float` | The gift card balance, float. |
| attributes.**formatted\_balance** | `string` | The gift card balance, formatted. |
| attributes.**balance\_max\_cents** | `string` | The gift card balance max, in cents. |
| attributes.**balance\_max\_float** | `float` | The gift card balance max, float. |
| attributes.**formatted\_balance\_max** | `string` | The gift card balance max, formatted. |
| attributes.**balance\_log** | `object` | The gift card balance log. Tracks all the gift card transactions. |
| attributes.**single\_use** | `boolean` | Indicates if the gift card can be used only one. |
| attributes.**rechargeable** | `boolean` | Indicates if the gift card can be recharged. |
| attributes.**image\_url** | `string` | The URL of an image that represents the gift card. |
| attributes.**expires\_at** | `datetime` | Time at which the gift card will expire. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**recipient\_email** | `string` | The email address of the associated recipient. When creating or updating a gift card, this is a shortcut to find or create the associated recipient by email. |
| attributes.**\_purchase** | `boolean, value is 'true'` | Send this attribute if you want to confirm a draft gift card. The gift card becomes 'inactive', waiting to be activated. |
| attributes.**\_activate** | `boolean, value is 'true'` | Send this attribute if you want to activate a gift card. |
| attributes.**\_deactivate** | `boolean, value is 'true'` | Send this attribute if you want to deactivate a gift card. |
| attributes.**\_balance\_change\_cents** | `integer` | The balance change, in cents. Send a negative value to reduces the card balance by the specified amount. Send a positive value to recharge the gift card \(if rechargeable\). |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**market** | `object` | The associated market \(optional\). |
| relationships.**gift\_card\_recipient** | `object` | The associated gift card recipient \(optional\). |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

