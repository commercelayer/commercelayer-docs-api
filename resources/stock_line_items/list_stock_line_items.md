---
description: How to fetch a collection of stock line items via API
---

# List all stock line items

To fetch a collection of stock line items, send a `GET` request to the `/api/stock_line_items` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/stock_line_items**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of stock line items:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/stock_line_items/ \
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
      "type": "stock_line_items",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/stock_line_items/xYZkjABcde"
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
        "shipment": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/stock_line_items/xYZkjABcde/relationships/shipment",
            "related": "https://yourdomain.commercelayer.io/api/stock_line_items/xYZkjABcde/shipment"
          }
        },
        "line_item": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/stock_line_items/xYZkjABcde/relationships/line_item",
            "related": "https://yourdomain.commercelayer.io/api/stock_line_items/xYZkjABcde/line_item"
          }
        },
        "stock_item": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/stock_line_items/xYZkjABcde/relationships/stock_item",
            "related": "https://yourdomain.commercelayer.io/api/stock_line_items/xYZkjABcde/stock_item"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 stock_line_items (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/stock_line_items?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/stock_line_items?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/stock_line_items?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of stock line items can be sorted by the following attributes:

* `quantity`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

