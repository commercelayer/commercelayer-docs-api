---
description: The credit card object and its fields
---

# Credit cards

Credit cards can be associated to orders as their payment sources. Customers can save their credit cards in their wallets \(as customer payment sources\).

## The credit card object

A **credit card** object is returned as part of the response body of each successful [create](https://docs.commercelayer.io/resources/credit_cards/create_credit_card), [list](https://docs.commercelayer.io/resources/credit_cards/list_credit_cards), [retrieve](https://docs.commercelayer.io/resources/credit_cards/retrieve_credit_card), or [update](https://docs.commercelayer.io/resources/credit_cards/update_credit_card) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `credit_cards` |
| **id** | `string` | The credit card unique identifier |
| links.**self** | `string` | The credit card endpoint URL |
| attributes.**first\_name** | `string` | The cardholder's first name |
| attributes.**last\_name** | `string` | The cardholder's last name |
| attributes.**full\_name** | `string` | Handy attribute that returns the cardholder's first and last name |
| attributes.**number** | `string` | The credit card number |
| attributes.**month** | `string` | The credit card expiration month |
| attributes.**year** | `string` | The credit card expiration year |
| attributes.**valid\_thru** | `string` | Handy attribute that returns 'month/year' |
| attributes.**verification\_value** | `string` | The credit card verification value \(CCV, CVV\) |
| attributes.**card\_type** | `string` | The credit card type, e.g. visa, master, american\_express |
| attributes.**display\_number** | `string` | The obscured credit card number. This can be useful to safely display an order's payment source details. |
| attributes.**name** | `string` | Alias for 'display\_number' |
| attributes.**display\_verification\_value** | `string` | The obscured credit card verification value. This can be useful to safely display an order's payment source details. |
| attributes.**fingerprint** | `string` | A universal unique identifier for the credit card |
| attributes.**storage\_state** | `string` | The credit card storage state within your vault. Can be one of 'cached', 'retained', or 'redacted'. |
| attributes.**id** | `string` | Unique identifier for the resource \(hash\). |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**order** | `object` | The order associated to the credit card. If present, the credit card is set as the order's payment source. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

