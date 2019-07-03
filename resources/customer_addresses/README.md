---
description: The customer address object and its fields
---

# Customer addresses

Customer addresses are association models that link customers to addresses.
Creating a customer address means adding an address to a customer's wallet.
During checkout, a logged customer can retrieve their saved addresses and use them as the order shipping or billing addresses.


### The customer address object

A **customer address** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/resources/customer_addresses/create_customer_address),
[list](https://docs.commercelayer.io/resources/customer_addresses/list_customer_addresses),
[retrieve](https://docs.commercelayer.io/resources/customer_addresses/retrieve_customer_address),
or [update](https://docs.commercelayer.io/resources/customer_addresses/update_customer_address) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `customer_addresses` |
| **id** | `string` | The customer address unique identifier |
| links.**self** | `string` | The customer address endpoint URL |
| attributes.**name** | `string` | Returns the associated address' name |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**customer** | `object` | The associated customer. |
| relationships.**address** | `object` | The associated address. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
