---
description: How to fetch a collection of price lists via API
---

# List all price lists

To fetch a collection of price lists, send a `GET` request to the `/api/price_lists` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/price_lists**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of price lists:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/price_lists/ \
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
      "type": "price_lists",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/price_lists/xYZkjABcde"
      },
      "attributes": {
        "name": "EU Price list",
        "currency_code": "EUR",
        "tax_included": "true",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "prices": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/price_lists/xYZkjABcde/relationships/prices",
            "related": "https://yourdomain.commercelayer.io/api/price_lists/xYZkjABcde/prices"
          }
        },
        "attachments": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/price_lists/xYZkjABcde/relationships/attachments",
            "related": "https://yourdomain.commercelayer.io/api/price_lists/xYZkjABcde/attachments"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 price_lists (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/price_lists?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/price_lists?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/price_lists?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of price lists can be sorted by the following attributes:

* `name`
* `currency_code`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

