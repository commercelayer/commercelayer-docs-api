---
description: The shipping method object and its fields
---

# Shipping methods

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

## The shipping method object

A **shipping\_method** object is returned as part of the response body of each successful [create](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/shipping_methods/create-shipping%20method.md), [list](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/shipping_methods/list-all-shipping%20methods.md), [retrieve](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/shipping_methods/retrieve-shipping%20method.md) or [update](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/shipping_methods/update-shipping%20method.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `shipping_methods` |
| **id** | `string` | The shipping method unique identifier |
| links.**self** | `string` | The shipping method endpoint URL |
| attributes.**name** | `string` | The shipping method's name |
| attributes.**disabled\_at** | `datetime` | Time at which the shipping method was disabled. |
| attributes.**currency\_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard, automatically inherited from the associated market. |
| attributes.**price\_amount\_cents** | `integer` | The price of this shipping method, in cents. |
| attributes.**price\_amount\_float** | `float` | The price of this shipping method, float. |
| attributes.**formatted\_price\_amount** | `string` | The price of this shipping method, formatted. |
| attributes.**free\_over\_amount\_cents** | `integer` | Apply free shipping if the order amount is over this value, in cents. |
| attributes.**free\_over\_amount\_float** | `float` | Apply free shipping if the order amount is over this value, float. |
| attributes.**formatted\_free\_over\_amount** | `string` | Apply free shipping if the order amount is over this value, formatted. |
| attributes.**price\_amount\_for\_shipment\_cents** | `integer` | The calculated price \(zero or price amount\) when associated to a shipment, in cents. |
| attributes.**price\_amount\_for\_shipment\_float** | `float` | The calculated price \(zero or price amount\) when associated to a shipment, float. |
| attributes.**formatted\_price\_amount\_for\_shipment** | `string` | The calculated price \(zero or price amount\) when associated to a shipment, formatted. |
| attributes.**id** | `string` | Unique identifier for the resource \(hash\). |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**market** | `object` | The market where this shipping method is available. |
| relationships.**shipping\_zone** | `object` | The shipping zone that is used to match the order shipping address. |
| relationships.**shipping\_category** | `object` | The shipping category for which this shipping method is available. |
| relationships.**delivery\_lead\_time\_for\_shipment** | `object` | The delivery lead time for the associated shipment. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

