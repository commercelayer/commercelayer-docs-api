---
description: How to fetch a collection of refunds via API
---

# List all refunds

To fetch a collection of refunds, send a `GET` request to the `/api/refunds` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/refunds**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of refunds:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/refunds/ \
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
      "type": "refunds",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/refunds/xYZkjABcde"
      },
      "attributes": {
        "number": null,
        "currency_code": "EUR",
        "amount_cents": 1500,
        "amount_float": 15.0,
        "formatted_amount": "€15,00",
        "succeeded": false,
        "message": null,
        "error_code": null,
        "error_detail": null,
        "token": null,
        "gateway_transaction_id": null,
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
            "self": "https://yourdomain.commercelayer.io/api/refunds/xYZkjABcde/relationships/order",
            "related": "https://yourdomain.commercelayer.io/api/refunds/xYZkjABcde/order"
          }
        },
        "reference_capture": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/refunds/xYZkjABcde/relationships/reference_capture",
            "related": "https://yourdomain.commercelayer.io/api/refunds/xYZkjABcde/reference_capture"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 refunds (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/refunds?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/refunds?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/refunds?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of refunds can be sorted by the following attributes:

* `number`
* `amount_cents`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

