---
description: How to fetch a collection of SKU list promotion rules via API
---

# List all SKU list promotion rules

To fetch a collection of SKU list promotion rules, send a `GET` request to the `/api/sku_list_promotion_rules` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/sku\_list\_promotion\_rules**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of SKU list promotion rules:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/sku_list_promotion_rules/ \
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
      "type": "sku_list_promotion_rules",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/sku_list_promotion_rules/xYZkjABcde"
      },
      "attributes": {
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        },
        "all_skus": true
      },
      "relationships": {
        "promotion": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/sku_list_promotion_rules/xYZkjABcde/relationships/promotion",
            "related": "https://yourdomain.commercelayer.io/api/sku_list_promotion_rules/xYZkjABcde/promotion"
          }
        },
        "sku_list": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/sku_list_promotion_rules/xYZkjABcde/relationships/sku_list",
            "related": "https://yourdomain.commercelayer.io/api/sku_list_promotion_rules/xYZkjABcde/sku_list"
          }
        },
        "skus": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/sku_list_promotion_rules/xYZkjABcde/relationships/skus",
            "related": "https://yourdomain.commercelayer.io/api/sku_list_promotion_rules/xYZkjABcde/skus"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 sku_list_promotion_rules (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/sku_list_promotion_rules?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/sku_list_promotion_rules?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/sku_list_promotion_rules?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of SKU list promotion rules can be sorted by the following attributes:

* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

