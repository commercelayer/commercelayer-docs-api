---
description: How to create a braintree payment via API
---

# Create a braintree payment

To create a new braintree payment, send a `POST` request to the `/api/braintree_payments` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/braintree_payments**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**options** | `object` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**order** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new braintree payment:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/braintree_payments \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "braintree_payments",
    "relationships": {
      "order": {
        "data": {
          "type": "orders",
          "id": "QWERtyUpBa"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created resource object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "braintree_payments",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/braintree_payments/xYZkjABcde"
    },
    "attributes": {
      "client_token": "xxxx.yyyy.zzzz",
      "payment_method_nonce": "xxxx.yyyy.zzzz",
      "options": {
        "customer_id": "1234567890"
      },
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "order": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/braintree_payments/xYZkjABcde/relationships/order",
          "related": "https://yourdomain.commercelayer.io/api/braintree_payments/xYZkjABcde/order"
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
