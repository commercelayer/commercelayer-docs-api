---
description: How to fetch a collection of stock locations via API
---

# List all stock locations

To fetch a collection of stock locations, send a `GET` request to the `/api/stock_locations` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/stock_locations**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of stock locations:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/stock_locations/ \
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
      "type": "stock_locations",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde"
      },
      "attributes": {
        "number": 1234,
        "name": "Primary warehouse",
        "label_format": "PDF",
        "suppress_etd": false,
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "address": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/address",
            "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/address"
          }
        },
        "inventory_stock_locations": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/inventory_stock_locations",
            "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/inventory_stock_locations"
          }
        },
        "inventory_return_locations": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/inventory_return_locations",
            "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/inventory_return_locations"
          }
        },
        "stock_items": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/stock_items",
            "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/stock_items"
          }
        },
        "stock_transfers": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/stock_transfers",
            "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/stock_transfers"
          }
        },
        "attachments": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/attachments",
            "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/attachments"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 stock_locations (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/stock_locations?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/stock_locations?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/stock_locations?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of stock locations can be sorted by the following attributes:

* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

