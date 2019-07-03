---
description: How to fetch a collection of stock levels via API
---

# List all stock levels

To fetch a collection of stock levels, send a `GET` request to the `/api/stock_levels` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/stock_levels**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of stock levels:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/stock_levels/ \
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
      "priority": "1",
      "on_hold": "false",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    {
      "other": "... 9 stock levels (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/stock_levels?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/stock_levels?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/stock_levels?page[number]=14&page[size]=10"
  }
}


{
  "data": [
    {
      "id": "xYZkjABcde",
      "type": "stock_levels",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde"
      },
      "attributes": {
        "priority": "1",
        "on_hold": "false",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANYREFEFERNCE",
        "metadata": {
  "foo": "bar"
},
      },
      "relationships": {
        "stock_location": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde/relationships/stock_location",
              "related": "https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde/stock_location"
          }
        },
        "inventory_model": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde/relationships/inventory_model",
              "related": "https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde/inventory_model"
          }
        },
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 stock levels (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/stock_levels?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/stock_levels?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/stock_levels?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of stock levels can be sorted by the following attributes:

* `priority`
* `on_hold`
* `id`
* `created_at`
* `updated_at`
* `reference`

{% page-ref page="../../sorting-results.md" %}
