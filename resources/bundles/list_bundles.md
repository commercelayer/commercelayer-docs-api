---
description: How to fetch a collection of bundles via API
---

# List all bundles

To fetch a collection of bundles, send a `GET` request to the `/api/bundles` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/bundles**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of bundles:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/bundles/ \
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
      "type": "bundles",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde"
      },
      "attributes": {
        "code": "BUNDMM000000FFFFFFXLXX",
        "name": "Black Men T-shirt (XL) with Black Cap and Socks, all with White Logo",
        "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        "image_url": "https://img.yourdomain.com/bundles/xYZkjABcde.png",
        "price_amount_cents": 10000,
        "price_amount_float": 100.0,
        "formatted_price_amount": "€100,00",
        "compare_at_amount_cents": 13000,
        "compare_at_amount_float": 130.0,
        "formatted_compare_at_amount": "€130,00",
        "skus_count": 2,
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "market": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde/relationships/market",
            "related": "https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde/market"
          }
        },
        "sku_list": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde/relationships/sku_list",
            "related": "https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde/sku_list"
          }
        },
        "skus": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde/relationships/skus",
            "related": "https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde/skus"
          }
        },
        "attachments": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde/relationships/attachments",
            "related": "https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde/attachments"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 bundles (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/bundles?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/bundles?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/bundles?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of bundles can be sorted by the following attributes:

* `code`
* `price_amount_cents`
* `compare_at_amount_cents`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

