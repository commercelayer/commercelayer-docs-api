---
description: The customer object and its fields
---

# Customers

Customers must contain an email address and, optionally, a password. Registered customers can get an access token through the Password Flow to manage their data. Customer status can be one of "prospect," \(with no orders\) "acquired," \(with one order\), or "repeat" \(with two or more orders\). Customers can be associated with groups to get access to the related private markets \([learn more](https://docs.commercelayer.io/api/resources/customer_groups)\).

## The customer object

A **customer** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `customers` |
| **id** | `string` | The customer unique identifier |
| links.**self** | `string` | The customer endpoint URL |
| attributes.**email** | `string` | The customer's email address |
| attributes.**password** | `string` | The customer's password. Initiate a customer password reset flow if you need to change it. |
| attributes.**status** | `string` | The customer's status, one of 'prospect', 'acquired', or 'repeat'. |
| attributes.**has\_password** | `boolean` | Indicates if the customer has a password. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**customer\_group** | `object` | The group to which this customer belongs \(optional\). |
| relationships.**customer\_addresses** | `array` | The customer's saved addresses, i.e. their address book. |
| relationships.**customer\_payment\_sources** | `array` | The customer's saved creadit cards, i.e. their wallet. |
| relationships.**customer\_subscriptions** | `array` | The customer's subscriptions. |
| relationships.**orders** | `array` | The customer's orders, either pending or placed. |
| relationships.**returns** | `array` | The customer's returns, either pending or shipped. |
| relationships.**attachments** | `array` | The associated attachments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

