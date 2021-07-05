---
description: How to fetch a collection of SKU lists via API
---

# List all SKU lists

To fetch a collection of SKU lists, send a `GET` request to the `/api/sku_lists` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/sku_lists**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of SKU lists:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/sku_lists/ \
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
      "type": "sku_lists",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/sku_lists/xYZkjABcde"
      },
      "attributes": {
        "name": "Personal list",
        "slug": "personal-list-1",
        "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        "manual": false,
        "sku_code_regex": "^(A|B).*$",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "skus": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/sku_lists/xYZkjABcde/relationships/skus",
            "related": "https://yourdomain.commercelayer.io/api/sku_lists/xYZkjABcde/skus"
          }
        },
        "sku_list_items": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/sku_lists/xYZkjABcde/relationships/sku_list_items",
            "related": "https://yourdomain.commercelayer.io/api/sku_lists/xYZkjABcde/sku_list_items"
          }
        },
        "bundles": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/sku_lists/xYZkjABcde/relationships/bundles",
            "related": "https://yourdomain.commercelayer.io/api/sku_lists/xYZkjABcde/bundles"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 sku_lists (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/sku_lists?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/sku_lists?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/sku_lists?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of SKU lists can be sorted by the following attributes:

* `name`
* `slug`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

