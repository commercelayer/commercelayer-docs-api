---
description: How to request a specific sort for the results of a collection of resources
---

# Sorting results

When you fetch a collection of resources, you can request a specific sort for the results, using the `sort` query parameter.

{% hint style="warning" %}
The value of the `sort` parameter must be a comma-separated list of fields. Pay attention to avoid whitespaces before or after each comma.
{% endhint %}

{% hint style="info" %}
The sort order for each field is ascending unless prefixed with a `-` \(minus\) in which case it's descending.
{% endhint %}

### Example

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of SKUs sorted by their creation date \(descending\) and code:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/skus?sort=-created_at,code \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a paginated collection ****of the resource objects, sorted in the requested order:

```javascript
{
  "data": [
    {
      "id": "xYZkjABcde",
      "type": "skus",
      "links": {...},
      "attributes": {
        "code": "TSHIRTMM000000FFFFFFXLXX",
        "name": "Black Men T-shirt with White Logo (XL)",
        "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        "image_url": "https://img.yourdomain.com/skus/xYZkjABcde.png",
        "tag_names": "Men, Black, XL",
        "pieces_per_pack": 6,
        "weight": 300.0,
        "unit_of_weight": "gr",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANYREFEFERNCE",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "shipping_category": {
          "links": {...}
        },
        "prices": {
          "links": {...}
        },
        "stock_items": {
          "links": {...}
        },
        "delivery_lead_times": {
          "links": {...}
        },
        "sku_options": {
          "links": {...}
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 skus (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/skus?sort=-created_at,code&page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/skus?sort=-created_at,code&page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/skus?sort=-created_at,code&page[number]=14&page[size]=10"
  }
}
```

{% page-ref page="pagination.md" %}
{% endtab %}
{% endtabs %}

{% hint style="info" %}
You can get the full list of sortable attributes from the documentation of each resource.
{% endhint %}

