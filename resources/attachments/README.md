---
description: The attachment object and its fields
---

# Attachments

Attachments can be associated with any resource as a reference to any external document, through the `url` attribute.


### The attachment object

An **attachment** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/attachments/create_attachment),
[list](https://docs.commercelayer.io/api/resources/attachments/list_attachments),
[retrieve](https://docs.commercelayer.io/api/resources/attachments/retrieve_attachment),
or [update](https://docs.commercelayer.io/api/resources/attachments/update_attachment) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `attachments` |
| **id** | `string` | The attachment unique identifier |
| links.**self** | `string` | The attachment endpoint URL |

| attributes.**name** | `string` | The internal name of the attachment. |

| attributes.**description** | `string` | An internal description of the attachment. |

| attributes.**url** | `string` | The attachment URL. |

| attributes.**created_at** | `datetime` | Time at which the resource was created. |

| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |

| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |

| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |

| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**attachable** | `object` | The resource the attachment belongs to |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

