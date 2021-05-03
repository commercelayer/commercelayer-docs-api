---
description: The address object and its fields
---

# Addresses

Addresses can be associated with orders as their shipping or billing addresses. Add a Google or Bing geocoder to a market if you want its addresses to be automatically geocoded. Customers can save their most-used addresses in their address books \(as customer addresses\).

## The address object

An **address** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `addresses` |
| **id** | `string` | The address unique identifier |
| links.**self** | `string` | The address endpoint URL |
| attributes.**business** | `boolean` | Indicates if it's a business or a personal address |
| attributes.**first\_name** | `string` | Address first name \(personal\) |
| attributes.**last\_name** | `string` | Address last name \(personal\) |
| attributes.**company** | `string` | Address company name \(business\) |
| attributes.**full\_name** | `string` | Company name \(business\) of first name and last name \(personal\) |
| attributes.**line\_1** | `string` | Address line 1, i.e. Street address, PO Box |
| attributes.**line\_2** | `string` | Address line 2, i.e. Apartment, Suite, Building |
| attributes.**city** | `string` | Address city |
| attributes.**zip\_code** | `string` | ZIP or postal code |
| attributes.**state\_code** | `string` | State, province or region code. |
| attributes.**country\_code** | `string` | The international 2-letter country code as defined by the ISO 3166-1 standard |
| attributes.**phone** | `string` | Phone number \(including extension\). |
| attributes.**full\_address** | `string` | Compact description of the address location, without the full name |
| attributes.**name** | `string` | Compact description of the address location, including the full name |
| attributes.**email** | `string` | Email address. |
| attributes.**notes** | `string` | A free notes attached to the address. When used as a shipping address, this can be useful to let the customers add specific delivery instructions. |
| attributes.**lat** | `float` | The address geocoded latitude. This is automatically generated when creating a shipping/billing address for an order and a valid geocoder is attached to the order's market. |
| attributes.**lng** | `float` | The address geocoded longitude. This is automatically generated when creating a shipping/billing address for an order and a valid geocoder is attached to the order's market. |
| attributes.**is\_localized** | `boolean` | Indicates if the latitude and logitude are present, either geocoded or manually updated |
| attributes.**is\_geocoded** | `boolean` | Indicates if the address has been successfully geocoded |
| attributes.**provider\_name** | `string` | The geocoder provider name \(either Google or Bing\) |
| attributes.**map\_url** | `string` | The map url of the geocoded address \(if geocoded\) |
| attributes.**static\_map\_url** | `string` | The static map image url of the geocoded address \(if geocoded\) |
| attributes.**billing\_info** | `string` | Customer's billing information \(i.e. VAT number, codice fiscale\) |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**geocoder** | `object` | The geocoder attached to the address, to be used for geocoding. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

