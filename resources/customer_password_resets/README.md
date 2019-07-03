---
description: The customer password reset object and its fields
---

# Customer password resets

Customer passwords can be reset in three steps:

1. Create a new customer password reset with the email of the customer.
2. Get the reset password token from the response.
3. Update the customer password reset resource passing the token and the new password.

It's your responsibility to verify the customer's identity before third step.
A typical flow is to send an email to the customer with a verification link that includes the reset password token.


### The customer password reset object

A **customer password reset** object is returned as part of the response body of each successful [create](create-customer password reset.md), [list](list-all-customer password resets.md), [retrieve](retrieve-customer password reset.md) or [update](update-customer password reset.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `customer_password_resets` |
| **id** | `string` | The customer password reset unique identifier |
| links.**self** | `string` | The customer password reset endpoint URL |
| attributes.**customer_email** | `string` | The email of the customer that requires a password reset |
| attributes.**reset_password_token** | `string` | Automatically generated on create. Send its value as the '_reset_password_token' argument when updating the customer password. |
| attributes.**customer_password** | `string` | The customer new password. This will be accepted only if a valid '_reset_password_token' is sent with the request. |
| attributes.**_reset_password_token** | `string` | Send the 'reset_password_token' that you got on create when updating the customer password. |
| attributes.**reset_password_at** | `datetime` | Time at which the password was reset. |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**customer** | `object` | The customer that requires a password reset. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
