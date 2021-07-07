---
description: How to fetch a collection of external tax calculators via API
---

# List all external tax calculators

To fetch a collection of external tax calculators, send a `GET` request to the `/api/external_tax_calculators` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/external\_tax\_calculators**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of external tax calculators:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/external_tax_calculators/ \
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
      "type": "external_tax_calculators",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/external_tax_calculators/xYZkjABcde"
      },
      "attributes": {
        "name": "Personal tax calculator",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        },
        "tax_calculator_url": "https://external_calculator.yourbrand.com"
      },
      "relationships": {
        "tax_categories": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/external_tax_calculators/xYZkjABcde/relationships/tax_categories",
            "related": "https://yourdomain.commercelayer.io/api/external_tax_calculators/xYZkjABcde/tax_categories"
          }
        },
        "attachments": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/external_tax_calculators/xYZkjABcde/relationships/attachments",
            "related": "https://yourdomain.commercelayer.io/api/external_tax_calculators/xYZkjABcde/attachments"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 external_tax_calculators (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/external_tax_calculators?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/external_tax_calculators?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/external_tax_calculators?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of external tax calculators can be sorted by the following attributes:

* `name`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

