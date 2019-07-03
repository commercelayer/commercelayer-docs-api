---
description: The customer object and its fields
---

# Customers

Customers must contain an email address and, optionally, a password.
Registered customers can get an access token through the Password Flow to manage their data.
Customer status can be one of "prospect," (with no orders) "acquired," (with one order) or "repeat" (with two or more orders).
Associate a customer to a customer group if you want to assign a dedicated price list to that customer (<a href="/api/reference/customer_groups/">learn more</a>).


### The customer object

A **customer** object is returned as part of the response body of each successful [create](create-customer.md), [list](list-all-customers.md), [retrieve](retrieve-customer.md) or [update](update-customer.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `customers` |
| **id** | `string` | The customer unique identifier |
| links.**self** | `string` | The customer endpoint URL |
| attributes.**email** | `string` | The customer's email address |
| attributes.**password** | `string` | The customer's password. Initiate a customer password reset flow if you need to change it. |
| attributes.**status** | `string` | The customer's status, one of 'prospect', 'acquired', or 'repeat'. |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**customer_group** | `object` | The group to which this customer belongs (optional). |
| relationships.**customer_addresses** | `array` | The customer's saved addresses, i.e. their address book. |
| relationships.**customer_payment_sources** | `array` | The customer's saved creadit cards, i.e. their wallet. |
| relationships.**customer_subscriptions** | `array` | The customer's subscriptions. |
| relationships.**orders** | `array` | The customer's orders, either pending or placed. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
