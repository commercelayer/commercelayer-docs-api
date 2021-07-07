---
description: How to fetch a collection of manual tax calculators via API
---

# List all manual tax calculators

To fetch a collection of manual tax calculators, send a `GET` request to the `/api/manual_tax_calculators` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/manual\_tax\_calculators**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of manual tax calculators:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/manual_tax_calculators/ \
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
      "type": "manual_tax_calculators",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/manual_tax_calculators/xYZkjABcde"
      },
      "attributes": {
        "name": "Personal tax calculator",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "tax_categories": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/manual_tax_calculators/xYZkjABcde/relationships/tax_categories",
            "related": "https://yourdomain.commercelayer.io/api/manual_tax_calculators/xYZkjABcde/tax_categories"
          }
        },
        "attachments": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/manual_tax_calculators/xYZkjABcde/relationships/attachments",
            "related": "https://yourdomain.commercelayer.io/api/manual_tax_calculators/xYZkjABcde/attachments"
          }
        },
        "tax_rules": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/manual_tax_calculators/xYZkjABcde/relationships/tax_rules",
            "related": "https://yourdomain.commercelayer.io/api/manual_tax_calculators/xYZkjABcde/tax_rules"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 manual_tax_calculators (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/manual_tax_calculators?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/manual_tax_calculators?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/manual_tax_calculators?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of manual tax calculators can be sorted by the following attributes:

* `name`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

