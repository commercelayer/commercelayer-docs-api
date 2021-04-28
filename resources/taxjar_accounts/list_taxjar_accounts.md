---
description: How to fetch a collection of taxjar accounts via API
---

# List all taxjar accounts

To fetch a collection of taxjar accounts, send a `GET` request to the `/api/taxjar_accounts` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/taxjar\_accounts**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of taxjar accounts:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/taxjar_accounts/ \
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
      "type": "taxjar_accounts",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/taxjar_accounts/xYZkjABcde"
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
            "self": "https://yourdomain.commercelayer.io/api/taxjar_accounts/xYZkjABcde/relationships/tax_categories",
            "related": "https://yourdomain.commercelayer.io/api/taxjar_accounts/xYZkjABcde/tax_categories"
          }
        },
        "attachments": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/taxjar_accounts/xYZkjABcde/relationships/attachments",
            "related": "https://yourdomain.commercelayer.io/api/taxjar_accounts/xYZkjABcde/attachments"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 taxjar_accounts (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/taxjar_accounts?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/taxjar_accounts?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/taxjar_accounts?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of taxjar accounts can be sorted by the following attributes:

* `name`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`
* `api_key`

{% page-ref page="../../sorting-results.md" %}

