---
description: The organization object and its fields
---

# Organization

Your business company is identified by the related organization. This is a singleton API, meaning only the organization within the current scope it’s retrieved. No need to specify the resource id.


### The organization object

The **organization** object is returned as part of the response body of each successful retrieve API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `organization` |
| **id** | `string` | The organization unique identifier |
| links.**self** | `string` | The organization endpoint URL |
| attributes.**name** | `string` | The organization's internal name. |
| attributes.**slug** | `string` | The organization's slug name. |
| attributes.**domain** | `string` | The organization's domain. |
| attributes.**support_phone** | `string` | The organization's support phone. |
| attributes.**support_email** | `string` | The organization's support email. |
| attributes.**logo_url** | `string` | The URL to the organization's logo. |
| attributes.**favicon_url** | `string` | The URL to the organization's favicon. |
| attributes.**primary_color** | `string` | The organization's primary color. |
| attributes.**contrast_color** | `string` | The organization's contrast color. |
| attributes.**gtm_id** | `string` | The organization's Google Tag Manager ID. |
| attributes.**gtm_id_test** | `string` | The organization's Google Tag Manager ID for test. |
| attributes.**discount_disabled** | `boolean` | Indicates if organization has discount disabled. |
| attributes.**account_disabled** | `boolean` | Indicates if organization has account disabled. |
| attributes.**acceptance_disabled** | `boolean` | Indicates if organization has acceptance disabled. |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

