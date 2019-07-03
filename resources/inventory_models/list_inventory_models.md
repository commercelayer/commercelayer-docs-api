---
description: How to fetch a collection of inventory models via API
---

# List all inventory models

To fetch a collection of inventory models, send a `GET` request to the `/api/inventory_models` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/inventory_models**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of inventory models:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/inventory_models/ \
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
      "type": "inventory_models",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/inventory_models/xYZkjABcde"
      },
      "attributes": {
        "name": "EU Inventory Model"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
      },
      "relationships": {
        "stock_levels": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/inventory_models/xYZkjABcde/relationships/stock_levels",
              "related": "https://yourdomain.commercelayer.io/api/inventory_models/xYZkjABcde/stock_levels"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 inventory models (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/inventory_models?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/inventory_models?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/inventory_models?page[number]=14&page[size]=10"
  }
}
```

{% page-ref page="../../pagination.md" %}
{% endtab %}
{% endtabs %}

### Sortable attributes

The list of inventory models can be sorted by the following attributes:

* `name`
* `id`
* `created_at`
* `updated_at`
* `reference`

{% page-ref page="../../sorting-results.md" %}