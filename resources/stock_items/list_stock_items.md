---
description: How to fetch a collection of stock items via API
---

# List all stock items

To fetch a collection of stock items, send a `GET` request to the `/api/stock_items` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/stock\_items**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of stock items:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/stock_items/ \
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
      "type": "stock_items",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/stock_items/xYZkjABcde"
      },
      "attributes": {
        "sku_code": "TSHIRTMM000000FFFFFFXLXX",
        "quantity": 100,
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "stock_location": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/stock_items/xYZkjABcde/relationships/stock_location",
            "related": "https://yourdomain.commercelayer.io/api/stock_items/xYZkjABcde/stock_location"
          }
        },
        "sku": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/stock_items/xYZkjABcde/relationships/sku",
            "related": "https://yourdomain.commercelayer.io/api/stock_items/xYZkjABcde/sku"
          }
        },
        "attachments": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/stock_items/xYZkjABcde/relationships/attachments",
            "related": "https://yourdomain.commercelayer.io/api/stock_items/xYZkjABcde/attachments"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 stock_items (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/stock_items?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/stock_items?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/stock_items?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of stock items can be sorted by the following attributes:

* `quantity`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

