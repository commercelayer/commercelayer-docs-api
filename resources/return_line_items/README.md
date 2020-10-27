---
description: The return line item object and its fields
---

# Return line items

Create a return line item if you want to add an SKU to a return. You can restock the SKU within a return line item once the return has been marked as "received".

## The return line item object

A **return line item** object is returned as part of the response body of each successful create, list, retrieve, or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `return_line_items` |
| **id** | `string` | The return line item unique identifier |
| links.**self** | `string` | The return line item endpoint URL |
| attributes.**sku\_code** | `string` | The code of the associated sku. |
| attributes.**name** | `string` | The name of the line item. |
| attributes.**quantity** | `integer` | The line item quantity. |
| attributes.**\_restock** | `boolean, value is 'true'` | Send this attribute if you want to restock the line item. |
| attributes.**return\_reason** | `object` | Set of key-value pairs that you can use to add details about return reason. |
| attributes.**restocked\_at** | `datetime` | Time at which the return line item was restocked. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**return** | `object` | The associated return. |
| relationships.**line\_item** | `object` | The associated line item. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

