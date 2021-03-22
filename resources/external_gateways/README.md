---
description: The external gateway object and its fields
---

# External gateways

Connect the External payment gateway in order to be able to safely process any type of external payments.

## The external gateway object

An **external gateway** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `external_gateways` |
| **id** | `string` | The external gateway unique identifier |
| links.**self** | `string` | The external gateway endpoint URL |
| attributes.**name** | `string` | The payment gateway's internal name. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| attributes.**shared\_secret** | `string` | The shared secret used to sign gateway payloads. |
| attributes.**authorize\_url** | `string` | The endpoint used by the external gateway to authorize payments. |
| attributes.**capture\_url** | `string` | The endpoint used by the external gateway to capture payments. |
| attributes.**void\_url** | `string` | The endpoint used by the external gateway to void payments. |
| attributes.**refund\_url** | `string` | The endpoint used by the external gateway to refund payments. |
| relationships.**payment\_methods** | `array` | The associated payment methods. |
| relationships.**external\_payments** | `array` | The associated payments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

