---
description: How to update an existing parcel line item via API
---

# Update a parcel line item

To update an existing parcel line item, send a `PATCH` request to the `/api/parcel_line_items/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/parcel_line_items/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the parcel line item identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/parcel_line_items/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "parcel_line_items",
    "id": "xYZkjABcde",
    "attributes": {
      "reference": "ANY-EXTERNAL-REFEFERNCE"
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning the updated resource object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "parcel_line_items",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/parcel_line_items/xYZkjABcde"
    },
    "attributes": {
      "sku_code": "TSHIRTMM000000FFFFFFXLXX",
      "quantity": 4,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "parcel": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/parcel_line_items/xYZkjABcde/relationships/parcel",
          "related": "https://yourdomain.commercelayer.io/api/parcel_line_items/xYZkjABcde/parcel"
        }
      },
      "stock_line_item": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/parcel_line_items/xYZkjABcde/relationships/stock_line_item",
          "related": "https://yourdomain.commercelayer.io/api/parcel_line_items/xYZkjABcde/stock_line_item"
        }
      },
      "shipment_line_item": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/parcel_line_items/xYZkjABcde/relationships/shipment_line_item",
          "related": "https://yourdomain.commercelayer.io/api/parcel_line_items/xYZkjABcde/shipment_line_item"
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

