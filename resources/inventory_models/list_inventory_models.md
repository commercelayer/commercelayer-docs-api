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
        "name": "EU Inventory Model",
        "strategy": "split_shipments",
        "stock_locations_cutoff": "3",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "inventory_stock_locations": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/inventory_models/xYZkjABcde/relationships/inventory_stock_locations",
            "related": "https://yourdomain.commercelayer.io/api/inventory_models/xYZkjABcde/inventory_stock_locations"
          }
        },
        "inventory_return_locations": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/inventory_models/xYZkjABcde/relationships/inventory_return_locations",
            "related": "https://yourdomain.commercelayer.io/api/inventory_models/xYZkjABcde/inventory_return_locations"
          }
        },
        "attachments": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/inventory_models/xYZkjABcde/relationships/attachments",
            "related": "https://yourdomain.commercelayer.io/api/inventory_models/xYZkjABcde/attachments"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 inventory_models (first page)"
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
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of inventory models can be sorted by the following attributes:

* `name`
* `strategy`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

