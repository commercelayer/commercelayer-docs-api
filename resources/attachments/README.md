---
description: The attachment object and its fields
---

# Attachments

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

### The Attachment object

An attachment object is returned as part of the response body of each successful [create](create-attachment.md), [list](list-all-attachments.md), [retrieve](retrieve-attachment.md) or [update](update-attachment.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `attachments` |
| **id** | `string` | The attachment unique identifier |
| links.**self** | `string` | The attachment endpoint URL |
| attributes.**name** | `string` | The internal name of the attachment. |
| attributes.**description** | `string` | An internal description of the attachment. |
| attributes.**url** | `string` | The attachment URL. |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**attachable** | `has_one` | The resource the attachment belongs to |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
