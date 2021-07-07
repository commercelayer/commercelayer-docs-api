---
description: How to fetch a collection of returns via API
---

# List all returns

To fetch a collection of returns, send a `GET` request to the `/api/returns` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/returns**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of returns:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/returns/ \
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
      "type": "returns",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde"
      },
      "attributes": {
        "number": "#1234/R/001",
        "status": "draft",
        "customer_email": "john@example.com",
        "skus_count": 2,
        "approved_at": "2018-01-01T12:00:00.000Z",
        "cancelled_at": "2018-01-01T12:00:00.000Z",
        "shipped_at": "2018-01-01T12:00:00.000Z",
        "rejected_at": "2018-01-01T12:00:00.000Z",
        "received_at": "2018-01-01T12:00:00.000Z",
        "archived_at": "2018-01-01T12:00:00.000Z",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "order": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/relationships/order",
            "related": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/order"
          }
        },
        "customer": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/relationships/customer",
            "related": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/customer"
          }
        },
        "stock_location": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/relationships/stock_location",
            "related": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/stock_location"
          }
        },
        "origin_address": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/relationships/origin_address",
            "related": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/origin_address"
          }
        },
        "destination_address": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/relationships/destination_address",
            "related": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/destination_address"
          }
        },
        "return_line_items": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/relationships/return_line_items",
            "related": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/return_line_items"
          }
        },
        "attachments": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/relationships/attachments",
            "related": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/attachments"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 returns (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/returns?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/returns?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/returns?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of returns can be sorted by the following attributes:

* `status`
* `approved_at`
* `cancelled_at`
* `shipped_at`
* `rejected_at`
* `received_at`
* `archived_at`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

