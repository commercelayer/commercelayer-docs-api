---
description: How to fetch a collection of SKU list items via API
---

# List all SKU list items

To fetch a collection of SKU list items, send a `GET` request to the `/api/sku_list_items` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/sku_list_items**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of SKU list items:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/sku_list_items/ \
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
      "type": "sku_list_items",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/sku_list_items/xYZkjABcde"
      },
      "attributes": {
        "position": 2,
        "quantity": 1,
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "sku_list": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/sku_list_items/xYZkjABcde/relationships/sku_list",
            "related": "https://yourdomain.commercelayer.io/api/sku_list_items/xYZkjABcde/sku_list"
          }
        },
        "sku": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/sku_list_items/xYZkjABcde/relationships/sku",
            "related": "https://yourdomain.commercelayer.io/api/sku_list_items/xYZkjABcde/sku"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 sku_list_items (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/sku_list_items?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/sku_list_items?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/sku_list_items?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of SKU list items can be sorted by the following attributes:

* `position`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

