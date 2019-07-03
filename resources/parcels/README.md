---
description: The parcel object and its fields
---

# Parcels

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

## The parcel object

A **parcel** object is returned as part of the response body of each successful [create](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/parcels/create-parcel.md), [list](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/parcels/list-all-parcels.md), [retrieve](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/parcels/retrieve-parcel.md) or [update](https://github.com/commercelayer/commercelayer_docs/tree/59b0b081d713240e5ebab57aa88930add73d23e7/resources/parcels/update-parcel.md) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `parcels` |
| **id** | `string` | The parcel unique identifier |
| links.**self** | `string` | The parcel endpoint URL |
| attributes.**number** | `string` | Unique identified for the parcel |
| attributes.**weight** | `float` | The parcel weight, used to automatically calculate the tax rates from the available carrier accounts. |
| attributes.**unit\_of\_weight** | `string` | The unit of weight. Can be one of 'gr', or 'oz'. |
| attributes.**eel\_pfc** | `string` | When shipping outside the US, you need to provide either an Exemption and Exclusion Legend \(EEL\) code or a Proof of Filing Citation \(PFC\). Which you need is based on the value of the goods being shipped. Value can be one of "EEL" o "PFC". |
| attributes.**contents\_type** | `string` | The type of item you are sending. Can be one of 'merchandise', 'gift', 'documents', 'returned\_goods', 'sample', or 'other'. |
| attributes.**contents\_explanation** | `string` | If you specify 'other' in the 'contents\_type' attribute, you must supply a brief description in this attribute. |
| attributes.**customs\_certify** | `boolean` | Indicates if the provided information is accurate |
| attributes.**customs\_signer** | `string` | This is the name of the person who is certifying that the information provided on the customs form is accurate. Use a name of the person in your organization who is responsible for this. |
| attributes.**non\_delivery\_option** | `string` | In case the shipment cannot be delivered, this option tells the carrier what you want to happen to the parcel. You can pass either 'return', or 'abandon'. The value defaults to 'return'. If you pass 'abandon', you will not receive the parcel back if it cannot be delivered. |
| attributes.**restriction\_type** | `string` | Describes if your parcel requires any special treatment or quarantine when entering the country. Can be one of 'none', 'other', 'quarantine', or 'sanitary\_phytosanitary\_inspection'. |
| attributes.**restriction\_comments** | `string` | If you specify 'other' in the restriction type, you must supply a brief description of what is required. |
| attributes.**customs\_info\_required** | `boolean` | Indicates if the parcel requires customs info to get the shipping rates. |
| attributes.**shipping\_label\_url** | `string` | The shipping label url, ready to be downloaded and printed. |
| attributes.**shipping\_label\_file\_type** | `string` | The shipping label file type. One of 'application/pdf', 'application/zpl', 'application/epl2', or 'image/png'. |
| attributes.**shipping\_label\_size** | `string` | The shipping label size. |
| attributes.**shipping\_label\_resolution** | `string` | The shipping label resolution. |
| attributes.**tracking\_number** | `string` | The tracking number associated to this parcel. |
| attributes.**tracking\_status** | `string` | The tracking status for this parcel, automatically updated in real time by the shipping carrier. |
| attributes.**tracking\_status\_detail** | `string` | Additional information about the tracking status, automatically updated in real time by the shipping carrier. |
| attributes.**tracking\_status\_updated\_at** | `datetime` | Time at which the parcel's tracking status was last updated. |
| attributes.**tracking\_details** | `string` | The parcel's full tracking history, automatically updated in real time by the shipping carrier. |
| attributes.**carrier\_weight\_oz** | `string` | The weight of the parcel as measured by the carrier in ounces \(if available\) |
| attributes.**signed\_by** | `string` | The name of the person who signed for the parcel \(if available\) |
| attributes.**id** | `string` | Unique identifier for the resource \(hash\). |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**shipment** | `object` | The associated shipment. |
| relationships.**parcel\_line\_items** | `array` | The line items in this parcel \(a subset of the shipment line items\) |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

