---
description: The return object and its fields
---

# Returns

Returns are linked to one specific order. They get created in "draft" status and become "pending" when a customer requests to return SKUs from an order. Pending returns can be "approved" or "rejected". An approved return becomes "shipped" once it leaves the customer address. Returns are marked "received" once they reach the available return location, where they can be restocked to an inventory location.


### The return object

A **return** object is returned as part of the response body of each successful create, list, retrieve, or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `returns` |
| **id** | `string` | The return unique identifier |
| links.**self** | `string` | The return endpoint URL |
| attributes.**number** | `string` | Unique identifier for the return |
| attributes.**status** | `string` | The return status, one of 'draft', 'requested', 'approved', 'rejected', 'shipped' or 'received' |
| attributes.**customer_email** | `string` | The email address of the associated customer. |
| attributes.**skus_count** | `integer` | The total number of skus in the return's line items. This can be useful to display a preview of the return content. |
| attributes.**approved_at** | `datetime` | Time at which the return was approved. |
| attributes.**rejected_at** | `datetime` | Time at which the return was rejected. |
| attributes.**shipped_at** | `datetime` | Time at which the return was shipped. |
| attributes.**received_at** | `datetime` | Time at which the return was received. |
| attributes.**archived_at** | `datetime` | Time at which the resource has been archived. |
| attributes.**_request** | `boolean, value is 'true'` | Send this attribute if you want to activate this return. |
| attributes.**_approve** | `boolean, value is 'true'` | Send this attribute if you want to mark this return as approved. |
| attributes.**_reject** | `boolean, value is 'true'` | Send this attribute if you want to mark this return as rejected. |
| attributes.**_ship** | `boolean, value is 'true'` | Send this attribute if you want to mark this return as shipped. |
| attributes.**_receive** | `boolean, value is 'true'` | Send this attribute if you want to mark this return as received. |
| attributes.**_restock** | `boolean, value is 'true'` | Send this attribute if you want to restock all of the return line items. |
| attributes.**_archive** | `boolean, value is 'true'` | Send this attribute if you want to archive the return. |
| attributes.**_unarchive** | `boolean, value is 'true'` | Send this attribute if you want to unarchive the return. |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**order** | `object` | The associated order. |
| relationships.**customer** | `object` | The associated customer. |
| relationships.**stock_location** | `object` | The stock location to which the return will be shipped. |
| relationships.**origin_address** | `object` | The customer shipping address. |
| relationships.**destination_address** | `object` | The associated stock location address. |
| relationships.**return_line_items** | `array` | The order line items associated to the return. |
| relationships.**attachments** | `array` | The associated attachments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

