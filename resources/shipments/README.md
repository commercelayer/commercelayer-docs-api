---
description: The shipment object and its fields
---

# Shipments

An order can be split into more shipments for one of the following reasons:

- The order contains line items from more than one stock location
- The order contains line items belonging to more than one shipping category

The combination of stock locations and shipping categories determines the number of shipments. Each shipment gets fulfilled separately.


### The shipment object

A **shipment** object is returned as part of the response body of each successful list, retrieve or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `shipments` |
| **id** | `string` | The shipment unique identifier |
| links.**self** | `string` | The shipment endpoint URL |
| attributes.**number** | `string` | Unique identifier for the shipment |
| attributes.**status** | `string` | The shipment status, one of 'draft', 'upcoming', 'cancelled', 'on_hold', 'picking', 'packing', 'ready_to_ship', or 'shipped' |
| attributes.**currency_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard, automatically inherited from the associated order. |
| attributes.**cost_amount_cents** | `integer` | The cost of this shipment from the selected carrier account, in cents. |
| attributes.**cost_amount_float** | `float` | The cost of this shipment from the selected carrier account, float. |
| attributes.**formatted_cost_amount** | `string` | The cost of this shipment from the selected carrier account, formatted. |
| attributes.**skus_count** | `integer` | The total number of skus in the shipment's line items. This can be useful to display a preview of the shipment content. |
| attributes.**_on_hold** | `boolean, value is 'true'` | Send this attribute if you want to put this shipment on hold. |
| attributes.**_picking** | `boolean, value is 'true'` | Send this attribute if you want to start picking this shipment. |
| attributes.**_packing** | `boolean, value is 'true'` | Send this attribute if you want to start packing this shipment. |
| attributes.**_ready_to_ship** | `boolean, value is 'true'` | Send this attribute if you want to mark this shipment as ready to ship. |
| attributes.**_ship** | `boolean, value is 'true'` | Send this attribute if you want to mark this shipment as shipped. |
| attributes.**_get_rates** | `boolean, value is 'true'` | Send this attribute if you want get the shipping rates from the associated carrier accounts. |
| attributes.**selected_rate_id** | `string` | The selected purchase rate from the available shipping rates. |
| attributes.**rates** | `object` | The available shipping rates. |
| attributes.**_purchase** | `boolean, value is 'true'` | Send this attribute if you want to purchase this shipment with the selected rate. |
| attributes.**purchase_error_code** | `string` | The shipping rate purchase error code, if any. |
| attributes.**purchase_error_message** | `string` | The shipping rate purchase error message, if any. |
| attributes.**get_rates_started_at** | `datetime` | Time at which the getting of the shipping rates started. |
| attributes.**get_rates_completed_at** | `datetime` | Time at which the getting of the shipping rates completed. |
| attributes.**purchase_started_at** | `datetime` | Time at which the purchasing of the shipping rate started. |
| attributes.**purchase_completed_at** | `datetime` | Time at which the purchasing of the shipping rate completed. |
| attributes.**purchase_failed_at** | `datetime` | Time at which the purchasing of the shipping rate failed. |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**order** | `object` | The associated order. |
| relationships.**shipping_category** | `object` | The shipping category of the associated line items (skus). |
| relationships.**stock_location** | `object` | The stock location from which the shipment is managed. |
| relationships.**origin_address** | `object` | The associated stock location address. |
| relationships.**shipping_address** | `object` | The customer shipping address. |
| relationships.**shipping_method** | `object` | The shipping method selected by the customer. |
| relationships.**delivery_lead_time** | `object` | The delivery lead time for the shipment. Equals the one associated with the shipping method selected by the customer. |
| relationships.**shipment_line_items** | `array` | The order line items assigned to the shipment. |
| relationships.**stock_transfers** | `array` | The associated stock transfers. |
| relationships.**available_shipping_methods** | `array` | The available shipping methods for the shipment. Useful to present the customer with a list of choices during the checkout. Only enabled shipping methods are included in the list. |
| relationships.**carrier_accounts** | `array` | The carrier accounts available for the order's market. |
| relationships.**parcels** | `array` | The associated parcels. |
| relationships.**attachments** | `array` | The associated attachments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

