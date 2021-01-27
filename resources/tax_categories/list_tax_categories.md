---
description: How to fetch a collection of tax categories via API
---

# List all tax categories

To fetch a collection of tax categories, send a `GET` request to the `/api/tax_categories` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/tax\_categories**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of tax categories:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/tax_categories/ \
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
      "type": "tax_categories",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/tax_categories/xYZkjABcde"
      },
      "attributes": {
        "code": "31000",
        "sku_code": "TSHIRTMM000000FFFFFFXLXX",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "sku": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/tax_categories/xYZkjABcde/relationships/sku",
            "related": "https://yourdomain.commercelayer.io/api/tax_categories/xYZkjABcde/sku"
          }
        },
        "tax_calculator": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/tax_categories/xYZkjABcde/relationships/tax_calculator",
            "related": "https://yourdomain.commercelayer.io/api/tax_categories/xYZkjABcde/tax_calculator"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 tax_categories (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/tax_categories?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/tax_categories?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/tax_categories?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of tax categories can be sorted by the following attributes:

* `code`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

