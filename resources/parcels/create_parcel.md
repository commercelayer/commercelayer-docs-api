---
description: How to create a parcel via API
---

# Create a parcel

To create a new parcel, send a `POST` request to the `/api/parcels` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/parcels**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**weight** | `float` | Optional |
| attributes.**unit_of_weight** | `string` | Optional |
| attributes.**eel_pfc** | `string` | Optional |
| attributes.**contents_type** | `string` | Optional |
| attributes.**contents_explanation** | `string` | Optional |
| attributes.**customs_certify** | `boolean` | Optional |
| attributes.**customs_signer** | `string` | Optional |
| attributes.**non_delivery_option** | `string` | Optional |
| attributes.**restriction_type** | `string` | Optional |
| attributes.**restriction_comments** | `string` | Optional |
| attributes.**customs_info_required** | `boolean` | Optional, default 'false' |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**shipment** | `object` | Required |

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
          "id": "QWERtyUpBa"
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
      "number": "#1234/S/001/P/001",
      "weight": "1000",
      "unit_of_weight": "gr",
      "eel_pfc": "EEL",
      "contents_type": "merchandise",
      "contents_explanation": "",
      "customs_certify": "false",
      "customs_signer": "John Doe",
      "non_delivery_option": "return",
      "restriction_type": "none",
      "restriction_comments": "",
      "customs_info_required": "false",
      "shipping_label_url": "https://bucket.s3-us-west-2.amazonaws.com/files/postage_label/20180101/123.pdf",
      "shipping_label_file_type": "application/pdf",
      "shipping_label_size": "4x7",
      "shipping_label_resolution": "200",
      "tracking_number": "1Z4V2A000000000000",
      "tracking_status": "delivered",
      "tracking_status_detail": "arrived_at_destination",
      "tracking_status_updated_at": "2018-01-01T12:00:00.000Z",
      "tracking_details": "",
      "carrier_weight_oz": "42.32",
      "signed_by": "John Smith",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "shipment": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/parcels/xYZkjABcde/relationships/shipment",
          "related": "https://yourdomain.commercelayer.io/api/parcels/xYZkjABcde/shipment"
        }
      },
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
