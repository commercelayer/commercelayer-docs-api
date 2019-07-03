---
description: The shipment object and its fields
---

# Shipments

An order can be split into more shipments for one of the following reasons:

* The order contains line items from more than one stock location.
* The order contains line items belonging to more than one shipping category.

The combination of stock locations and shipping categories determine the number of shipments. Each shipment gets fulfilled separately.

## The shipment object

A **shipment** object is returned as part of the response body of each successful [create](https://docs.commercelayer.io/api/resources/shipments/create_shipment), [list](https://docs.commercelayer.io/api/resources/shipments/list_shipments), [retrieve](https://docs.commercelayer.io/api/resources/shipments/retrieve_shipment), or [update](https://docs.commercelayer.io/api/resources/shipments/update_shipment) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `shipments` |
| **id** | `string` | The shipment unique identifier |
| links.**self** | `string` | The shipment endpoint URL |
| attributes.**number** | `string` | Unique identified for the shipment |
| attributes.**status** | `string` | The shipment status, one of 'draft', 'upcoming', 'cancelled', 'on\_hold', 'picking', 'packing', 'ready\_to\_ship', or 'shipped' |
| attributes.**currency\_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard, automatically inherited from the associated order. |
| attributes.**cost\_amount\_cents** | `integer` | The cost of this shipment from the selected carrier account, in cents. |
| attributes.**cost\_amount\_float** | `float` | The cost of this shipment from the selected carrier account, float. |
| attributes.**formatted\_cost\_amount** | `string` | The cost of this shipment from the selected carrier account, formatted. |
| attributes.**\_on\_hold** | `integer, value is '1'` | Send this attribute if you want to put this shipment on hold. |
| attributes.**\_picking** | `integer, value is '1'` | Send this attribute if you want to start picking this shipment. |
| attributes.**\_packing** | `integer, value is '1'` | Send this attribute if you want to start packing this shipment. |
| attributes.**\_ready\_to\_ship** | `integer, value is '1'` | Send this attribute if you want to mark this shipment as ready to ship. |
| attributes.**\_ship** | `integer, value is '1'` | Send this attribute if you want to mark this shipment as shipped. |
| attributes.**\_get\_rates** | `integer, value is '1'` | Send this attribute if you want get the shipping rates from the associated carrier accounts. |
| attributes.**selected\_rate\_id** | `string` | The selected purchase rate from the available shipping rates. |
| attributes.**\_purchase** | `integer, value is '1'` | Send this attribute if you want to purchase this shipment with the selected rate. |
| attributes.**id** | `string` | Unique identifier for the resource \(hash\). |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**shipping\_category** | `object` | The shipping category of the associated line items \(skus\). |
| relationships.**stock\_location** | `object` | The stock location from which the shipment is managed. |
| relationships.**shipping\_address** | `object` | The customer shipping address. |
| relationships.**shipping\_method** | `object` | The shipping method selected by the customer. |
| relationships.**shipment\_line\_items** | `array` | The order line items assigned to the shipment. |
| relationships.**available\_shipping\_methods** | `array` | The available shipping methods for the shipment. Useful to present the customer with a list of choices during the checkout. Only enabled shipping methods are included in the list. |
| relationships.**parcels** | `array` | The parcels associated to the shipment. |
| relationships.**attachments** | `array` | The attachments associated to the shipment. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

