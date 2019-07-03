---
description: How to fetch a collection of SKUs via API
---

# List all SKUs

To fetch a collection of SKUs, send a `GET` request to the `/api/skus` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/skus**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of SKUs:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/skus/ \
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
      "code": "TSHIRTMM000000FFFFFFXLXX",
      "name": "Black Men T-shirt with White Logo (XL)",
      "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
      "image_url": "https://img.yourbrand.com/skus/xYZkjABcde.png",
      "tag_names": "Men, Black, XL",
      "pieces_per_pack": "6",
      "weight": "300",
      "unit_of_weight": "gr",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    {
      "other": "... 9 SKUs (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/skus?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/skus?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/skus?page[number]=14&page[size]=10"
  }
}


{
  "data": [
    {
      "id": "xYZkjABcde",
      "type": "skus",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde"
      },
      "attributes": {
        "code": "TSHIRTMM000000FFFFFFXLXX",
        "name": "Black Men T-shirt with White Logo (XL)",
        "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        "image_url": "https://img.yourbrand.com/skus/xYZkjABcde.png",
        "tag_names": "Men, Black, XL",
        "pieces_per_pack": "6",
        "weight": "300",
        "unit_of_weight": "gr",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANYREFEFERNCE",
        "metadata": {
  "foo": "bar"
},
      },
      "relationships": {
        "shipping_category": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/shipping_category",
              "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/shipping_category"
          }
        },
        "prices": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/prices",
              "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/prices"
          }
        },
        "stock_items": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/stock_items",
              "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/stock_items"
          }
        },
        "delivery_lead_times": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/delivery_lead_times",
              "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/delivery_lead_times"
          }
        },
        "sku_options": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/sku_options",
              "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/sku_options"
          }
        },
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 SKUs (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/skus?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/skus?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/skus?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of SKUs can be sorted by the following attributes:

* `code`
* `id`
* `created_at`
* `updated_at`
* `reference`

{% page-ref page="../../sorting-results.md" %}

