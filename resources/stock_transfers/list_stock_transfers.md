---
description: How to fetch a collection of stock transfers via API
---

# List all stock transfers

To fetch a collection of stock transfers, send a `GET` request to the `/api/stock_transfers` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/stock\_transfers**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of stock transfers:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/stock_transfers/ \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a paginated collection of resource objects:

```javascript
{
  "data": [
    {
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
    },
    {
      "other": "... 9 stock_transfers (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/stock_transfers?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/stock_transfers?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/stock_transfers?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of stock transfers can be sorted by the following attributes:

* `status`
* `completed_at`
* `cancelled_at`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

