---
description: How to fetch a specific braintree payment via API
---

# Retrieve a braintree payment

To fetch a single braintree payment, send a `GET` request to the `/api/braintree_payments/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/braintree_payments/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the braintree payment identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/braintree_payments/xYZkjABcde \
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
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
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

