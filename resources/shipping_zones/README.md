---
description: The shipping zone object and its fields
---

# Shipping zones

Shipping zones determine the available shipping methods for a given shipping address. The match is evaluated against a set of regular expressions on the address country, state, or zip code.

## The shipping zone object

A **shipping zone** object is returned as part of the response body of each successful create, list, retrieve, or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `shipping_zones` |
| **id** | `string` | The shipping zone unique identifier |
| links.**self** | `string` | The shipping zone endpoint URL |
| attributes.**name** | `string` | The shipping zone's internal name. |
| attributes.**country\_code\_regex** | `string` | The regex that will be evaluated to match the shipping address country code. |
| attributes.**not\_country\_code\_regex** | `string` | The regex that will be evaluated as negative match for the shipping address country code. |
| attributes.**state\_code\_regex** | `string` | The regex that will be evaluated to match the shipping address state code. |
| attributes.**not\_state\_code\_regex** | `string` | The regex that will be evaluated as negative match for the shipping address state code. |
| attributes.**zip\_code\_regex** | `string` | The regex that will be evaluated to match the shipping address zip code. |
| attributes.**not\_zip\_code\_regex** | `string` | The regex that will be evaluated as negative match for the shipping zip country code. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**attachments** | `array` | The associated attachments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

