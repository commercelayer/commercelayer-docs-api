---
description: The shipment object and its fields
---

# Shipments

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

### The shipment object

A **shipment** object is returned as part of the response body of each successful [create](create-shipment.md), [list](list-all-shipments.md), [retrieve](retrieve-shipment.md) or [update](update-shipment.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `shipments` |
| **id** | `string` | The shipment unique identifier |
| links.**self** | `string` | The shipment endpoint URL |
| attributes.**number** | `string` | Unique identified for the shipment |
| attributes.**status** | `string` | The shipment status, one of 'draft', 'upcoming', 'cancelled', 'on_hold', 'picking', 'packing', 'ready_to_ship', or 'shipped' |
| attributes.**currency_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard, automatically inherited from the associated order. |
| attributes.**cost_amount_cents** | `integer` | The cost of this shipment from the selected carrier account, in cents. |
| attributes.**cost_amount_float** | `float` | The cost of this shipment from the selected carrier account, float. |
| attributes.**formatted_cost_amount** | `string` | The cost of this shipment from the selected carrier account, formatted. |
| attributes.**_on_hold** | `integer, value is '1'` | Send this attribute if you want to put this shipment on hold. |
| attributes.**_picking** | `integer, value is '1'` | Send this attribute if you want to start picking this shipment. |
| attributes.**_packing** | `integer, value is '1'` | Send this attribute if you want to start packing this shipment. |
| attributes.**_ready_to_ship** | `integer, value is '1'` | Send this attribute if you want to mark this shipment as ready to ship. |
| attributes.**_ship** | `integer, value is '1'` | Send this attribute if you want to mark this shipment as shipped. |
| attributes.**_get_rates** | `integer, value is '1'` | Send this attribute if you want get the shipping rates from the associated carrier accounts. |
| attributes.**selected_rate_id** | `string` | The selected purchase rate from the available shipping rates. |
| attributes.**_purchase** | `integer, value is '1'` | Send this attribute if you want to purchase this shipment with the selected rate. |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**shipping_category** | `object` | The shipping category of the associated line items (skus). |
| relationships.**stock_location** | `object` | The stock location from which the shipment is managed. |
| relationships.**shipping_address** | `object` | The customer shipping address. |
| relationships.**shipping_method** | `object` | The shipping method selected by the customer. |
| relationships.**shipment_line_items** | `array` | The order line items assigned to the shipment. |
| relationships.**available_shipping_methods** | `array` | The available shipping methods for the shipment. Useful to present the customer with a list of choices during the checkout. Only enabled shipping methods are included in the list. |
| relationships.**parcels** | `array` | The parcels associated to the shipment. |
| relationships.**attachments** | `array` | The attachments associated to the shipment. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
