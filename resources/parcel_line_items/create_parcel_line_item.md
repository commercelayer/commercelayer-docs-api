---
description: How to create a parcel line item via API
---

# Create a parcel line item

To create a new parcel line item, send a `POST` request to the `/api/parcel_line_items` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain.commercelayer.io**/api/parcel\_line\_items**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**sku\_code** | `string` | Optional |
| attributes.**quantity** | `integer` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**parcel** | `object` | Required |
| relationships.**stock\_line\_item** | `object` | Required |
| relationships.**shipment\_line\_item** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new parcel line item:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/parcel_line_items \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "parcel_line_items",
    "attributes": {
      "quantity": null
    },
    "relationships": {
      "parcel": {
        "data": {
          "type": "parcels",
          "id": "QWERtyUpBa"
        }
      },
      "stock_line_item": {
        "data": {
          "type": "stock_line_items",
          "id": "QWERtyUpBa"
        }
      },
      "shipment_line_item": {
        "data": {
          "type": "shipment_line_items",
          "id": "QWERtyUpBa"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created resource object:

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
      "quantity": 0,
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

