---
description: How to fetch a collection of inventory return locations via API
---

# List all inventory return locations

To fetch a collection of inventory return locations, send a `GET` request to the `/api/inventory_return_locations` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/inventory\_return\_locations**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of inventory return locations:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/inventory_return_locations/ \
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
      "type": "inventory_return_locations",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/inventory_return_locations/xYZkjABcde"
      },
      "attributes": {
        "priority": "1",
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
            "self": "https://yourdomain.commercelayer.io/api/inventory_return_locations/xYZkjABcde/relationships/stock_location",
            "related": "https://yourdomain.commercelayer.io/api/inventory_return_locations/xYZkjABcde/stock_location"
          }
        },
        "inventory_model": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/inventory_return_locations/xYZkjABcde/relationships/inventory_model",
            "related": "https://yourdomain.commercelayer.io/api/inventory_return_locations/xYZkjABcde/inventory_model"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 inventory_return_locations (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/inventory_return_locations?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/inventory_return_locations?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/inventory_return_locations?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of inventory return locations can be sorted by the following attributes:

* `priority`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

