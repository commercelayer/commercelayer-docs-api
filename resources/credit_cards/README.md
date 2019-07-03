---
description: The credit card object and its fields
---

# Credit cards

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

## The credit card object

A **credit\_card** object is returned as part of the response body of each successful [create](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/credit_cards/create-credit%20card.md), [list](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/credit_cards/list-all-credit%20cards.md), [retrieve](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/credit_cards/retrieve-credit%20card.md) or [update](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/credit_cards/update-credit%20card.md) API call.

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
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**order** | `object` | The order associated to the credit card. If present, the credit card is set as the order's payment source. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

