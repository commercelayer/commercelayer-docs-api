---
description: The billing info validation rule object and its fields
---

# Billing info validation rules

Billing info validation rules are a type of order validation rules that let you make the billing info required for a specific market.


### The billing info validation rule object

A **billing info validation rule** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/billing_info_validation_rules/create_billing_info_validation_rule),
[list](https://docs.commercelayer.io/api/resources/billing_info_validation_rules/list_billing_info_validation_rules),
[retrieve](https://docs.commercelayer.io/api/resources/billing_info_validation_rules/retrieve_billing_info_validation_rule),
or [update](https://docs.commercelayer.io/api/resources/billing_info_validation_rules/update_billing_info_validation_rule) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `billing_info_validation_rules` |
| **id** | `string` | The billing info validation rule unique identifier |
| links.**self** | `string` | The billing info validation rule endpoint URL |

| attributes.**created\_at** | `datetime` | Time at which the resource was created. |

| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |

| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |

| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |

| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**market** | `object` | The associated market. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

