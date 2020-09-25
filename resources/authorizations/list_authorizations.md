---
description: How to fetch a collection of authorizations via API
---

# List all authorizations

To fetch a collection of authorizations, send a `GET` request to the `/api/authorizations` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/authorizations**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of authorizations:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/authorizations/ \
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
      "type": "authorizations",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/authorizations/xYZkjABcde"
      },
      "attributes": {
        "number": null,
        "currency_code": "EUR",
        "amount_cents": "1500",
        "amount_float": "15.0",
        "formatted_amount": "€15,00",
        "succeeded": "false",
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
        },
        "cvv_code": null,
        "cvv_message": null,
        "avs_code": null,
        "avs_message": null,
        "fraud_review": null,
        "capture_amount_cents": "500",
        "capture_amount_float": "5.0",
        "formatted_capture_amount": "€5,00",
        "capture_balance_cents": "1000",
        "capture_balance_float": "10.0",
        "formatted_capture_balance": "€10,00",
        "void_balance_cents": "1500",
        "void_balance_float": "15.0",
        "formatted_void_balance": "€15,00"
      },
      "relationships": {
        "order": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/authorizations/xYZkjABcde/relationships/order",
            "related": "https://yourdomain.commercelayer.io/api/authorizations/xYZkjABcde/order"
          }
        },
        "captures": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/authorizations/xYZkjABcde/relationships/captures",
            "related": "https://yourdomain.commercelayer.io/api/authorizations/xYZkjABcde/captures"
          }
        },
        "voids": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/authorizations/xYZkjABcde/relationships/voids",
            "related": "https://yourdomain.commercelayer.io/api/authorizations/xYZkjABcde/voids"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 authorizations (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/authorizations?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/authorizations?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/authorizations?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of authorizations can be sorted by the following attributes:

* `amount_cents`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

