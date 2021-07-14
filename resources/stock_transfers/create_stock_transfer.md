---
description: How to create a stock transfer via API
---

# Create a stock transfer

To create a new stock transfer, send a `POST` request to the `/api/stock_transfers` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/stock_transfers**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**sku_code** | `string` | Optional |
| attributes.**quantity** | `integer` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**sku** | `object` | Required |
| relationships.**origin_stock_location** | `object` | Required |
| relationships.**destination_stock_location** | `object` | Required |
| relationships.**shipment** | `object` | Optional |
| relationships.**line_item** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new stock transfer:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/stock_transfers \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "stock_transfers",
    "attributes": {
      "quantity": "2"
    },
    "relationships": {
      "sku": {
        "data": {
          "type": "skus",
          "id": "QWERtyUpBa"
        }
      },
      "origin_stock_location": {
        "data": {
          "type": "origin_stock_locations",
          "id": "QWERtyUpBa"
        }
      },
      "destination_stock_location": {
        "data": {
          "type": "destination_stock_locations",
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
    "type": "stock_transfers",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/stock_transfers/xYZkjABcde"
    },
    "attributes": {
      "sku_code": "TSHIRTMM000000FFFFFFXLXX",
      "status": "draft",
      "quantity": 2,
      "completed_at": "2018-01-01T12:00:00.000Z",
      "cancelled_at": "2018-01-01T12:00:00.000Z",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "sku": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stock_transfers/xYZkjABcde/relationships/sku",
          "related": "https://yourdomain.commercelayer.io/api/stock_transfers/xYZkjABcde/sku"
        }
      },
      "origin_stock_location": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stock_transfers/xYZkjABcde/relationships/origin_stock_location",
          "related": "https://yourdomain.commercelayer.io/api/stock_transfers/xYZkjABcde/origin_stock_location"
        }
      },
      "destination_stock_location": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stock_transfers/xYZkjABcde/relationships/destination_stock_location",
          "related": "https://yourdomain.commercelayer.io/api/stock_transfers/xYZkjABcde/destination_stock_location"
        }
      },
      "shipment": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stock_transfers/xYZkjABcde/relationships/shipment",
          "related": "https://yourdomain.commercelayer.io/api/stock_transfers/xYZkjABcde/shipment"
        }
      },
      "line_item": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stock_transfers/xYZkjABcde/relationships/line_item",
          "related": "https://yourdomain.commercelayer.io/api/stock_transfers/xYZkjABcde/line_item"
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

