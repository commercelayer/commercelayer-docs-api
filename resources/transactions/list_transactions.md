---
description: How to fetch a collection of transactions via API
---

# List all transactions

To fetch a collection of transactions, send a `GET` request to the `/api/transactions` endpoint.

## Request

**GET** https://yourdomain.commercelayer.io**/api/transactions**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of transactions:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/transactions/ \
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
      "type": "transactions",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/transactions/xYZkjABcde"
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
            "self": "https://yourdomain.commercelayer.io/api/transactions/xYZkjABcde/relationships/order",
            "related": "https://yourdomain.commercelayer.io/api/transactions/xYZkjABcde/order"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 transactions (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/transactions?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/transactions?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/transactions?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

### Sortable attributes

The list of transactions can be sorted by the following attributes:

* `number`
* `amount_cents`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

