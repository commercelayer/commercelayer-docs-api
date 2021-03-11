---
description: How to fetch a specific capture via API
---

# Retrieve a capture

To fetch a single capture, send a `GET` request to the `/api/captures/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/captures/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the capture identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/captures/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "captures",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/captures/xYZkjABcde"
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
      },
      "refund_amount_cents": 500,
      "refund_amount_float": 5.0,
      "formatted_refund_amount": "€5,00",
      "refund_balance_cents": 1000,
      "refund_balance_float": 10.0,
      "formatted_refund_balance": "€10,00"
    },
    "relationships": {
      "order": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/captures/xYZkjABcde/relationships/order",
          "related": "https://yourdomain.commercelayer.io/api/captures/xYZkjABcde/order"
        }
      },
      "reference_authorization": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/captures/xYZkjABcde/relationships/reference_authorization",
          "related": "https://yourdomain.commercelayer.io/api/captures/xYZkjABcde/reference_authorization"
        }
      },
      "refunds": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/captures/xYZkjABcde/relationships/refunds",
          "related": "https://yourdomain.commercelayer.io/api/captures/xYZkjABcde/refunds"
        }
      }
    },
    "meta": {
      "mode": "test"
    }
  }
}
```
{% endtab %}
{% endtabs %}

