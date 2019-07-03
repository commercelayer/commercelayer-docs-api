---
description: The webhook object and its fields
---

# Webhooks

Webhooks are used to send real time events to external listeners.
When a webhook is triggered, Commerce Layer sends a POST request to the webhook's callback URL.
The object in the request body has the same format that you get when fetching the resource through the API.


### The webhook object

A **webhook** object is returned as part of the response body of each successful
[create](/api-reference/resources/webhooks/create_webhook),
[list](/api-reference/resources/webhooks/list_webhooks),
[retrieve](/api-reference/resources/webhooks/retrieve_webhook),
or [update](/api-reference/resources/webhooks/update_webhook) API call.

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
