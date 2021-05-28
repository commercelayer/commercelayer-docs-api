---
description: How to fetch a collection of adjustments via API
---

# List all adjustments

To fetch a collection of adjustments, send a `GET` request to the `/api/adjustments` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/adjustments**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of adjustments:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/adjustments/ \
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
      "type": "adjustments",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/adjustments/xYZkjABcde"
      },
      "attributes": {
        "name": "Additional service",
        "currency_code": "EUR",
        "amount_cents": 1500,
        "amount_float": 15.0,
        "formatted_amount": "€15,00",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {},
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 adjustments (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/adjustments?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/adjustments?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/adjustments?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of adjustments can be sorted by the following attributes:

* `name`
* `currency_code`
* `amount_cents`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

