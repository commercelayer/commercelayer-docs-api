---
description: The application object and its fields
---

# Applications

OAuth Applications let you consume the API and build your integrations. This is a singleton API, meaning only the application within the current scope it’s retrieved. No need to specify the resource id.

## The application object

The **application** object is returned as part of the response body of each successful retrieve API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `application` |
| **id** | `string` | The application unique identifier |
| links.**self** | `string` | The application endpoint URL |
| attributes.**name** | `string` | The application's internal name. |
| attributes.**kind** | `string` | The application's kind, can be one of: 'sales\_channel', 'checkout', 'contentful', 'datocms', 'sanity', 'cli', 'integration', 'webapp', 'zapier', or 'channel' |
| attributes.**public\_access** | `string` | Indicates if the application has public access. |
| attributes.**redirect\_uri** | `string` | The application's redirect URI. |
| attributes.**uid** | `string` | The application's unique ID. |
| attributes.**secret** | `string` | The application's secret. |
| attributes.**scopes** | `string` | The application's scopes. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

