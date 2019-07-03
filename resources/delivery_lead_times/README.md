---
description: The delivery lead time object and its fields
---

# Delivery lead times

Delivery lead times provide customers with detailed information about their shipments.
This is useful if you ship from many stock locations or offer more shipping method options within a market (<a href="/glossary/delivery_lead_time/">learn more</a>).


### The delivery lead time object

A **delivery lead time** object is returned as part of the response body of each successful [create](create-delivery lead time.md), [list](list-all-delivery lead times.md), [retrieve](retrieve-delivery lead time.md) or [update](update-delivery lead time.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `delivery_lead_times` |
| **id** | `string` | The delivery lead time unique identifier |
| links.**self** | `string` | The delivery lead time endpoint URL |
| attributes.**min_hours** | `integer` | The delivery lead minimum time (in hours) when shipping from the associated stock location with the associated shipping method. |
| attributes.**max_hours** | `integer` | The delivery lead maximun time (in hours) when shipping from the associated stock location with the associated shipping method. |
| attributes.**min_days** | `integer` | The delivery lead minimum time, in days (rounded) |
| attributes.**max_days** | `integer` | The delivery lead maximun time, in days (rounded) |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**stock_location** | `object` | The associated stock location. |
| relationships.**shipping_method** | `object` | The associated shipping method. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
