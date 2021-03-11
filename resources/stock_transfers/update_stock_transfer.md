---
description: How to update an existing stock transfer via API
---

# Update a stock transfer

To update an existing stock transfer, send a `PATCH` request to the `/api/stock_transfers/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/stock_transfers/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**sku_code** | `string` | Optional |
| attributes.**_upcoming** | `boolean, value is 'true'` | Optional |
| attributes.**_picking** | `boolean, value is 'true'` | Optional |
| attributes.**_in_transit** | `boolean, value is 'true'` | Optional |
| attributes.**_complete** | `boolean, value is 'true'` | Optional |
| attributes.**_cancel** | `boolean, value is 'true'` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**sku** | `object` | Optional |
| relationships.**origin_stock_location** | `object` | Optional |
| relationships.**destination_stock_location** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the stock transfer identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/stock_transfers/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "stock_transfers",
    "id": "xYZkjABcde",
    "attributes": {
      "sku_code": "TSHIRTMM000000FFFFFFXLXX"
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

