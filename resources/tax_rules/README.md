---
description: The tax rule object and its fields
---

# Tax rules

Create a tax rule to be associated with a manual tax calculator. Use the available regular expressions to match the order shipping method and apply the specified tax rate.

## The tax rule object

A **tax rule** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `tax_rules` |
| **id** | `string` | The tax rule unique identifier |
| links.**self** | `string` | The tax rule endpoint URL |
| attributes.**name** | `string` | The tax rule internal name. |
| attributes.**tax\_rate** | `float` | The tax rate for this ruke. |
| attributes.**country\_code\_regex** | `string` | The regex that will be evaluated to match the shipping address country code. |
| attributes.**not\_country\_code\_regex** | `string` | The regex that will be evaluated as negative match for the shipping address country code. |
| attributes.**state\_code\_regex** | `string` | The regex that will be evaluated to match the shipping address state code. |
| attributes.**not\_state\_code\_regex** | `string` | The regex that will be evaluated as negative match for the shipping address state code. |
| attributes.**zip\_code\_regex** | `string` | The regex that will be evaluated to match the shipping address zip code. |
| attributes.**not\_zip\_code\_regex** | `string` | The regex that will be evaluated as negative match for the shipping zip country code. |
| attributes.**freight\_taxable** | `boolean` | Indicates if the freight is taxable. |
| attributes.**payment\_method\_taxable** | `boolean` | Indicates if the payment method is taxable. |
| attributes.**gift\_card\_taxable** | `boolean` | Indicates if gift cards are taxable. |
| attributes.**adjustment\_taxable** | `boolean` | Indicates if adjustemnts are taxable. |
| attributes.**breakdown** | `object` | The breakdown for this tax rule \(if calculated\). |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**manual\_tax\_calculator** | `object` | The associated manual tax calculator. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

