---
description: The webhook object and its fields
---

# Webhooks

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

### The Webhook object

A webhook object is returned as part of the response body of each successful [create](create-webhook.md), [list](list-all-webhooks.md), [retrieve](retrieve-webhook.md) or [update](update-webhook.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `webhooks` |
| **id** | `string` | The webhook unique identifier |
| links.**self** | `string` | The webhook endpoint URL |
| attributes.**topic** | `string` | The identifier of the resource/event that will trigger the webhook. |
| attributes.**callback_url** | `string` | URI where the webhook subscription should send the POST request when the event occurs. |
| attributes.**include_resources** | `array` | List of related resources that should be included in the webhook body. |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
