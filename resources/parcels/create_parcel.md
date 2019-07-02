---
description: How to create A parcel via API
---

# Create A parcel

To create a new parcel, send a `POST` request to the `/api/parcels` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain&#46;commercelayer&#46;io**/api/parcels**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**number** | `string` |  |
| attributes.**weight** | `float` | optional |
| attributes.**unit_of_weight** | `string` | optional |
| attributes.**eel_pfc** | `string` | optional |
| attributes.**contents_type** | `string` | optional |
| attributes.**contents_explanation** | `string` | optional |
| attributes.**customs_certify** | `boolean` | optional |
| attributes.**customs_signer** | `string` | optional |
| attributes.**non_delivery_option** | `string` | optional |
| attributes.**restriction_type** | `string` | optional |
| attributes.**restriction_comments** | `string` | optional |
| attributes.**customs_info_required** | `boolean` | optional, default 'false' |
| attributes.**shipping_label_url** | `string` | optional |
| attributes.**shipping_label_file_type** | `string` | optional |
| attributes.**shipping_label_size** | `string` | optional |
| attributes.**shipping_label_resolution** | `string` | optional |
| attributes.**tracking_number** | `string` | optional |
| attributes.**tracking_status** | `string` | optional |
| attributes.**tracking_status_detail** | `string` | optional |
| attributes.**tracking_status_updated_at** | `datetime` |  |
| attributes.**tracking_details** | `string` | optional |
| attributes.**carrier_weight_oz** | `string` |  |
| attributes.**signed_by** | `string` | optional |
| attributes.**id** | `string` | required |
| attributes.**created_at** | `datetime` | required |
| attributes.**updated_at** | `datetime` | required |
| attributes.**reference** | `string` | optional |
| attributes.**metadata** | `object` | optional |
| relationships.**shipment** | `has_one` | required |
| relationships.**parcel_line_items** | `has_many` |  |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new parcel:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/parcels \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "parcels",
    "attributes": {
    },
    "relationships": {
      "shipment": {
        "data": {
          "type": "shipments",
          "id": "zxcVBnMASd"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `parcel` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "parcels",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/parcels/xYZkjABcde"
    },
    "attributes": {
        "number": "#1234/S/001/P/001"
        "weight": "1000"
        "unit_of_weight": "gr"
        "eel_pfc": "EEL"
        "contents_type": "merchandise"
        "contents_explanation": ""
        "customs_certify": "false"
        "customs_signer": "John Doe"
        "non_delivery_option": "return"
        "restriction_type": "none"
        "restriction_comments": ""
        "customs_info_required": "false"
        "shipping_label_url": "https://bucket.s3-us-west-2.amazonaws.com/files/postage_label/20180101/123.pdf"
        "shipping_label_file_type": "application/pdf"
        "shipping_label_size": "4x7"
        "shipping_label_resolution": "200"
        "tracking_number": "1Z4V2A000000000000"
        "tracking_status": "delivered"
        "tracking_status_detail": "arrived_at_destination"
        "tracking_status_updated_at": "2018-01-01T12:00:00.000Z"
        "tracking_details": ""
        "carrier_weight_oz": "42.32"
        "signed_by": "John Smith"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
        "shipment": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/parcels/xYZkjABcde/relationships/shipment",
              "related": "https://yourdomain.commercelayer.io/api/parcels/xYZkjABcde/shipment"
          }
        }
        "parcel_line_items": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/parcels/xYZkjABcde/relationships/parcel_line_items",
              "related": "https://yourdomain.commercelayer.io/api/parcels/xYZkjABcde/parcel_line_items"
          }
        }
      },
      "meta": {
          "mode": "test"
      }
  }
}
```
{% endtab %}
{% endtabs %}
