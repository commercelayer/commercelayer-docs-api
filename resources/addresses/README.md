---
description: The address object and its fields
---

# Addresses

Addresses can be associated to orders as their shipping or billing addresses.
Add a Google or Bing geocoder to a market if you want its addresses to be automatically geocoded.
Customers can save their most used addresses in their address books (as customer addresses).


### The address object

An **address** object is returned as part of the response body of each successful
/api-reference/resources/addresses/create_address,
/api-reference/resources/addresses/list_addresses,
/api-reference/resources/addresses/retrieve_address,
or /api-reference/resources/addresses/update_address API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `addresses` |
| **id** | `string` | The address unique identifier |
| links.**self** | `string` | The address endpoint URL |
| attributes.**business** | `boolean` | Indicates if it's a business or a personal address |
| attributes.**first_name** | `string` | Address first name (personal) |
| attributes.**last_name** | `string` | Address last name (personal) |
| attributes.**company** | `string` | Address company name (business) |
| attributes.**full_name** | `string` | Company name (business) of first name and last name (personal) |
| attributes.**line_1** | `string` | Address line 1, i.e. Street address, PO Box |
| attributes.**line_2** | `string` | Address line 2, i.e. Apartment, Suite, Building |
| attributes.**city** | `string` | Address city |
| attributes.**zip_code** | `string` | ZIP or postal code |
| attributes.**state_code** | `string` | State, province or region code. |
| attributes.**country_code** | `string` | The international 2-letter country code as defined by the ISO 3166-1 standard |
| attributes.**phone** | `string` | Phone number (including extension). |
| attributes.**full_address** | `string` | Compact description of the address location, without the full name |
| attributes.**name** | `string` | Compact description of the address location, including the full name |
| attributes.**email** | `string` | Email address. |
| attributes.**notes** | `string` | A free notes attacched to the address. When used as a shipping address, this can be useful to let the customers add specific delivery instructions. |
| attributes.**lat** | `float` | The address geocoded latitude. This is automatically generated when creating a shipping/billing address for an order and a valid geocoder is attached to the order's market. |
| attributes.**lng** | `float` | The address geocoded longitude. This is automatically generated when creating a shipping/billing address for an order and a valid geocoder is attached to the order's market. |
| attributes.**is_localized** | `boolean` | Indicates if the latitude and logitude are present, either geocoded or manually updated |
| attributes.**is_geocoded** | `boolean` | Indicates if the address has been successfully geocoded |
| attributes.**provider_name** | `string` | The geocoder provider name (either Google or Bing) |
| attributes.**map_url** | `string` | The map url of the geocoded address (if geocoded) |
| attributes.**static_map_url** | `string` | The static map image url of the geocoded address (if geocoded) |
| attributes.**billing_info** | `string` | Customer's billing information (i.e. VAT number, codice fiscale) |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**geocoder** | `object` | The geocoder attached to the address, to be used for geocoding. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
