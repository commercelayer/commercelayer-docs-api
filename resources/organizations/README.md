---
description: The organization object and its fields
---

# Organizations

Organization identifies your business company. This is a singleton API, meaning only the organization within the current scope it's retrieved, no need to specify the resource ID.


### The organization object

An **organization** object is returned as part of the response body of each successful create, list, retrieve, or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `organizations` |
| **id** | `string` | The organization unique identifier |
| links.**self** | `string` | The organization endpoint URL |
| attributes.**name** | `string` | The organization's internal name. |
| attributes.**slug** | `string` | The organization's slug name. |
| attributes.**domain** | `string` | The organization's domain. |
| attributes.**logo_url** | `string` | The URL to the organization's logo. |
| attributes.**favicon_url** | `string` | The URL to the organization's favicon. |
| attributes.**primary_color** | `string` | The organization's primary color. |
| attributes.**ga_property_id** | `string` | The organization's Google Analytics ID. |
| attributes.**ga_property_id_test** | `string` | The organization's Google Analytics ID for test. |
| attributes.**discount_disabled** | `boolean` | Indicates if organization has discount disabled. |
| attributes.**account_disabled** | `boolean` | Indicates if organization has account disabled. |
| attributes.**acceptance_disabled** | `boolean` | Indicates if organization has acceptance disabled. |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

