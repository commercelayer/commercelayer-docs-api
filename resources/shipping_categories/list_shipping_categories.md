---
description: How to fetch a collection of shipping categories via API
---

# List all shipping categories

To fetch a collection of shipping categories, send a `GET` request to the `/api/shipping_categories` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/shipping_categories**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of shipping categories:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/shipping_categories/ \
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
      "type": "shipping_categories",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/shipping_categories/xYZkjABcde"
      },
      "attributes": {
        "name": "Merchandise"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{
  "foo": "bar"
}"
      },
      "relationships": {
        "skus": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/shipping_categories/xYZkjABcde/relationships/skus",
              "related": "https://yourdomain.commercelayer.io/api/shipping_categories/xYZkjABcde/skus"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 shipping categories (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/shipping_categories?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/shipping_categories?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/shipping_categories?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of shipping categories can be sorted by the following attributes:

* `name`
* `id`
* `created_at`
* `updated_at`
* `reference`

{% page-ref page="../../sorting-results.md" %}
