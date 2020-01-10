---
description: The shipping zone object and its fields
---

# Shipping zones

Shipping zones determine the available shipping methods for a given shipping address.
The match is evaluated against a set of regular expressions on the address country, state or zip code ([learn more](https://commercelayer.io/glossary/shipping_zone/)).


### The shipping zone object

A **shipping zone** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/shipping_zones/create_shipping_zone),
[list](https://docs.commercelayer.io/api/resources/shipping_zones/list_shipping_zones),
[retrieve](https://docs.commercelayer.io/api/resources/shipping_zones/retrieve_shipping_zone),
or [update](https://docs.commercelayer.io/api/resources/shipping_zones/update_shipping_zone) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `shipping_zones` |
| **id** | `string` | The shipping zone unique identifier |
| links.**self** | `string` | The shipping zone endpoint URL |
| attributes.**name** | `string` | The shipping zone's internal name. |
| attributes.**country_code_regex** | `string` | The regex that will be evaluated to match the shipping address country code. |
| attributes.**not_country_code_regex** | `string` | The regex that will be evaluated as negative match for the shipping address country code. |
| attributes.**state_code_regex** | `string` | The regex that will be evaluated to match the shipping address state code. |
| attributes.**not_state_code_regex** | `string` | The regex that will be evaluated as negative match for the shipping address state code. |
| attributes.**zip_code_regex** | `string` | The regex that will be evaluated to match the shipping address zip code. |
| attributes.**not_zip_code_regex** | `string` | The regex that will be evaluated as negative match for the shipping zip country code. |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
