---
description: The shipping method object and its fields
---

# Shipping methods

Shipping methods are used to provide customers with more delivery options. Each shipping method can have a price and can be free over a specific order's amount.


### The shipping method object

A **shipping method** object is returned as part of the response body of each successful create, list, retrieve, or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `shipping_methods` |
| **id** | `string` | The shipping method unique identifier |
| links.**self** | `string` | The shipping method endpoint URL |
| attributes.**name** | `string` | The shipping method's name |
| attributes.**disabled_at** | `datetime` | Time at which the shipping method was disabled. |
| attributes.**currency_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard, automatically inherited from the associated market. |
| attributes.**price_amount_cents** | `integer` | The price of this shipping method, in cents. |
| attributes.**price_amount_float** | `float` | The price of this shipping method, float. |
| attributes.**formatted_price_amount** | `string` | The price of this shipping method, formatted. |
| attributes.**free_over_amount_cents** | `integer` | Apply free shipping if the order amount is over this value, in cents. |
| attributes.**free_over_amount_float** | `float` | Apply free shipping if the order amount is over this value, float. |
| attributes.**formatted_free_over_amount** | `string` | Apply free shipping if the order amount is over this value, formatted. |
| attributes.**price_amount_for_shipment_cents** | `integer` | The calculated price (zero or price amount) when associated to a shipment, in cents. |
| attributes.**price_amount_for_shipment_float** | `float` | The calculated price (zero or price amount) when associated to a shipment, float. |
| attributes.**formatted_price_amount_for_shipment** | `string` | The calculated price (zero or price amount) when associated to a shipment, formatted. |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**market** | `object` | The market where this shipping method is available. |
| relationships.**shipping_zone** | `object` | The shipping zone that is used to match the order shipping address. |
| relationships.**shipping_category** | `object` | The shipping category for which this shipping method is available. |
| relationships.**delivery_lead_time_for_shipment** | `object` | The delivery lead time for the associated shipment. |
| relationships.**attachments** | `array` | The associated attachments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

