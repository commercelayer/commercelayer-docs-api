---
description: The customer object and its fields
---

# Customers

Customers must contain an email address and, optionally, a password. Registered customers can get an access token through the Password Flow to manage their data. Customer status can be one of "prospect," \(with no orders\) "acquired," \(with one order\) or "repeat" \(with two or more orders\). Associate a customer to a customer group if you want to assign a dedicated price list to that customer \([learn more](https://github.com/commercelayer/commercelayer_docs/tree/55d706e4a5e58279938d093575f2cf41845683f1/api-reference/resources/customer_groups/README.md)\).

## The customer object

A **customer** object is returned as part of the response body of each successful [create](https://docs.commercelayer.io/resources/customers/create_customer), [list](https://docs.commercelayer.io/resources/customers/list_customers), [retrieve](https://docs.commercelayer.io/resources/customers/retrieve_customer), or [update](https://docs.commercelayer.io/resources/customers/update_customer) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `customers` |
| **id** | `string` | The customer unique identifier |
| links.**self** | `string` | The customer endpoint URL |
| attributes.**email** | `string` | The customer's email address |
| attributes.**password** | `string` | The customer's password. Initiate a customer password reset flow if you need to change it. |
| attributes.**status** | `string` | The customer's status, one of 'prospect', 'acquired', or 'repeat'. |
| attributes.**id** | `string` | Unique identifier for the resource \(hash\). |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**customer\_group** | `object` | The group to which this customer belongs \(optional\). |
| relationships.**customer\_addresses** | `array` | The customer's saved addresses, i.e. their address book. |
| relationships.**customer\_payment\_sources** | `array` | The customer's saved creadit cards, i.e. their wallet. |
| relationships.**customer\_subscriptions** | `array` | The customer's subscriptions. |
| relationships.**orders** | `array` | The customer's orders, either pending or placed. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

