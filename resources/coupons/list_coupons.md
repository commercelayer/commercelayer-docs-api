---
description: How to fetch a collection of coupons via API
---

# List all coupons

To fetch a collection of coupons, send a `GET` request to the `/api/coupons` endpoint.

## Request

**GET** https://yourdomain.commercelayer.io**/api/coupons**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of coupons:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/coupons/ \
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
      "type": "coupons",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/coupons/xYZkjABcde"
      },
      "attributes": {
        "code": "04371af2-70b3-48d7-8f4e-316b374224c3",
        "usage_limit": 50,
        "usage_count": 20,
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "promotion_rule": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/coupons/xYZkjABcde/relationships/promotion_rule",
            "related": "https://yourdomain.commercelayer.io/api/coupons/xYZkjABcde/promotion_rule"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 coupons (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/coupons?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/coupons?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/coupons?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

### Sortable attributes

The list of coupons can be sorted by the following attributes:

* `code`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

