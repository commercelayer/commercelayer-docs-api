---
description: The authorization object and its fields
---

# Authorizations



### The authorization object

An **authorization** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/authorizations/create_authorization),
[list](https://docs.commercelayer.io/api/resources/authorizations/list_authorizations),
[retrieve](https://docs.commercelayer.io/api/resources/authorizations/retrieve_authorization),
or [update](https://docs.commercelayer.io/api/resources/authorizations/update_authorization) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `authorizations` |
| **id** | `string` | The authorization unique identifier |
| links.**self** | `string` | The authorization endpoint URL |
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
| attributes.**cvv_code** | `string` | The CVV code returned by the payment gateway |
| attributes.**cvv_message** | `string` | The CVV message returned by the payment gateway |
| attributes.**avs_code** | `string` | The AVS code returned by the payment gateway |
| attributes.**avs_message** | `string` | The AVS message returned by the payment gateway |
| attributes.**fraud_review** | `string` | The fraud review message, if any, returned by the payment gateway |
| attributes.**_capture** | `boolean, value is 'true'` | Send this attribute if you want to create a capture for this authorization. |
| attributes.**_capture_amount_cents** | `integer` | The associated capture amount, in cents. |
| attributes.**capture_amount_cents** | `integer` | The amount to be captured, in cents. |
| attributes.**capture_amount_float** | `float` | The amount to be captured, float. |
| attributes.**formatted_capture_amount** | `string` | The amount to be captured, formatted. |
| attributes.**capture_balance_cents** | `integer` | The balance to be captured, in cents. |
| attributes.**capture_balance_float** | `float` | The balance to be captured, float. |
| attributes.**formatted_capture_balance** | `string` | The balance to be captured, formatted. |
| attributes.**_void** | `boolean, value is 'true'` | Send this attribute if you want to create a void for this authorization. |
| attributes.**void_balance_cents** | `integer` | The balance to be voided, in cents. |
| attributes.**void_balance_float** | `float` | The balance to be voided, float. |
| attributes.**formatted_void_balance** | `string` | The balance to be voided, formatted. |
| relationships.**order** | `object` | The associated order |
| relationships.**captures** | `array` | The associated captures |
| relationships.**voids** | `array` | The associated voids |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

