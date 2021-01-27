---
description: How to fetch a specific stock transfer via API
---

# Retrieve a stock transfer

To fetch a single stock transfer, send a `GET` request to the `/api/stock_transfers/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/stock_transfers/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the stock transfer identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/stock_transfers/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

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
      "quantity": "2",
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

