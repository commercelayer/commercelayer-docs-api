---
description: How to fetch a collection of voids via API
---

# List all voids

To fetch a collection of voids, send a `GET` request to the `/api/voids` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/voids**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of voids:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/voids/ \
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
      "type": "voids",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/voids/xYZkjABcde"
      },
      "attributes": {
        "number": "42/T/001",
        "currency_code": "EUR",
        "amount_cents": 1500,
        "amount_float": 15.0,
        "formatted_amount": "€15,00",
        "succeeded": false,
        "message": "Accepted",
        "error_code": "00001",
        "error_detail": "Already settled",
        "token": "xxxx-yyyy-zzzz",
        "gateway_transaction_id": "xxxx-yyyy-zzzz",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "order": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/voids/xYZkjABcde/relationships/order",
            "related": "https://yourdomain.commercelayer.io/api/voids/xYZkjABcde/order"
          }
        },
        "reference_authorization": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/voids/xYZkjABcde/relationships/reference_authorization",
            "related": "https://yourdomain.commercelayer.io/api/voids/xYZkjABcde/reference_authorization"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 voids (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/voids?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/voids?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/voids?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of voids can be sorted by the following attributes:

* `number`
* `amount_cents`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

