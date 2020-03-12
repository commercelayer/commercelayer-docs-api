---
description: The parcel object and its fields
---

# Parcels

Shipments can be split into two or more parcels, that get tracked by the shipping carrier.
For cross-border shipments, you can fill in a customs form.
The related documentation is automatically generated and attached to the parcel.


### The parcel object

A **parcel** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/api/resources/parcels/create_parcel),
[list](https://docs.commercelayer.io/api/resources/parcels/list_parcels),
[retrieve](https://docs.commercelayer.io/api/resources/parcels/retrieve_parcel),
or [update](https://docs.commercelayer.io/api/resources/parcels/update_parcel) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `parcels` |
| **id** | `string` | The parcel unique identifier |
| links.**self** | `string` | The parcel endpoint URL |

| attributes.**number** | `string` | Unique identifier for the parcel |

| attributes.**weight** | `float` | The parcel weight, used to automatically calculate the tax rates from the available carrier accounts. |

| attributes.**unit_of_weight** | `string` | The unit of weight. Can be one of 'gr', or 'oz'. |

| attributes.**eel_pfc** | `string` | When shipping outside the US, you need to provide either an Exemption and Exclusion Legend (EEL) code or a Proof of Filing Citation (PFC). Which you need is based on the value of the goods being shipped. Value can be one of "EEL" o "PFC". |

| attributes.**contents_type** | `string` | The type of item you are sending. Can be one of 'merchandise', 'gift', 'documents', 'returned_goods', 'sample', or 'other'. |

| attributes.**contents_explanation** | `string` | If you specify 'other' in the 'contents_type' attribute, you must supply a brief description in this attribute. |

| attributes.**customs_certify** | `boolean` | Indicates if the provided information is accurate |

| attributes.**customs_signer** | `string` | This is the name of the person who is certifying that the information provided on the customs form is accurate. Use a name of the person in your organization who is responsible for this. |

| attributes.**non_delivery_option** | `string` | In case the shipment cannot be delivered, this option tells the carrier what you want to happen to the parcel. You can pass either 'return', or 'abandon'. The value defaults to 'return'. If you pass 'abandon', you will not receive the parcel back if it cannot be delivered. |

| attributes.**restriction_type** | `string` | Describes if your parcel requires any special treatment or quarantine when entering the country. Can be one of 'none', 'other', 'quarantine', or 'sanitary_phytosanitary_inspection'. |

| attributes.**restriction_comments** | `string` | If you specify 'other' in the restriction type, you must supply a brief description of what is required. |

| attributes.**customs_info_required** | `boolean` | Indicates if the parcel requires customs info to get the shipping rates. |

| attributes.**shipping_label_url** | `string` | The shipping label url, ready to be downloaded and printed. |

| attributes.**shipping_label_file_type** | `string` | The shipping label file type. One of 'application/pdf', 'application/zpl', 'application/epl2', or 'image/png'. |

| attributes.**shipping_label_size** | `string` | The shipping label size. |

| attributes.**shipping_label_resolution** | `string` | The shipping label resolution. |

| attributes.**tracking_number** | `string` | The tracking number associated to this parcel. |

| attributes.**tracking_status** | `string` | The tracking status for this parcel, automatically updated in real time by the shipping carrier. |

| attributes.**tracking_status_detail** | `string` | Additional information about the tracking status, automatically updated in real time by the shipping carrier. |

| attributes.**tracking_status_updated_at** | `datetime` | Time at which the parcel's tracking status was last updated. |

| attributes.**tracking_details** | `string` | The parcel's full tracking history, automatically updated in real time by the shipping carrier. |

| attributes.**carrier_weight_oz** | `string` | The weight of the parcel as measured by the carrier in ounces (if available) |

| attributes.**signed_by** | `string` | The name of the person who signed for the parcel (if available) |

| attributes.**created_at** | `datetime` | Time at which the resource was created. |

| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |

| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |

| attributes.**reference_origin** | `string` | Any identifier of the third party system that defines the reference code |

| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**shipment** | `object` | The associated shipment. |
| relationships.**parcel_line_items** | `array` | The line items in this parcel (a subset of the shipment line items) |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

