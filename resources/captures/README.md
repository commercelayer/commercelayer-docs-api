---
description: The capture object and its fields
---

# Captures



### The capture object

A **capture** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/captures/create_capture),
[list](https://docs.commercelayer.io/api/resources/captures/list_captures),
[retrieve](https://docs.commercelayer.io/api/resources/captures/retrieve_capture),
or [update](https://docs.commercelayer.io/api/resources/captures/update_capture) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `captures` |
| **id** | `string` | The capture unique identifier |
| links.**self** | `string` | The capture endpoint URL |
| attributes.**number** | `string` | The transaction number, auto generated |
| attributes.**currency_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard, inherited from the associated order. |
| attributes.**amount_cents** | `integer` | The transaction amount, in cents. |
| attributes.**amount_float** | `float` | The transaction amount, float. |
| attributes.**formatted_amount** | `string` | The transaction amount, formatted. |
| attributes.**succeeded** | `boolean` | Indicates if the transaction is successful |
| attributes.**message** | `string` | The message returned by the payment gateway |
| attributes.**error_code** | `string` | The error code, if any, returned by the payment gateway |
| attributes.**error_detail** | `string` | The error detail, if any, returned by the payment gateway |
| attributes.**token** | `string` | The token identifying the transaction, returned by the payment gateway |
| attributes.**gateway_transaction_id** | `string` | The ID identifying the transaction, returned by the payment gateway |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| attributes.**_refund** | `boolean, value is 'true'` | Send this attribute if you want to create a refund for this capture. |
| attributes.**_refund_amount_cents** | `integer` | The associated refund amount, in cents. |
| attributes.**refund_amount_cents** | `integer` | The amount to be refunded, in cents. |
| attributes.**refund_amount_float** | `float` | The amount to be refunded, float. |
| attributes.**formatted_refund_amount** | `string` | The amount to be refunded, formatted. |
| attributes.**refund_balance_cents** | `integer` | The balance to be refunded, in cents. |
| attributes.**refund_balance_float** | `float` | The balance to be refunded, float. |
| attributes.**formatted_refund_balance** | `string` | The balance to be refunded, formatted. |
| relationships.**order** | `object` | The associated order |
| relationships.**reference_authorization** | `object` | The associated reference authorization |
| relationships.**refunds** | `array` | The associated refunds |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

