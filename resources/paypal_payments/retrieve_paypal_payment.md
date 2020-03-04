---
description: How to fetch a specific paypal payment via API
---

# Retrieve a paypal payment

To fetch a single paypal payment, send a `GET` request to the `/api/paypal_payments/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/paypal\_payments/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the paypal payment identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/paypal_payments/xYZkjABcde \
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
    "type": "paypal_payments",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/paypal_payments/xYZkjABcde"
    },
    "attributes": {
      "return_url": "https://yourdomain.com/thankyou",
      "cancel_url": "https://yourdomain.com/checkout/payment",
      "note_to_payer": "Thank you for shopping with us!",
      "paypal_payer_id": "ABCDEFGHG123456",
      "name": "ABCDEFGHG123456",
      "paypal_id": "1234567890",
      "status": "created",
      "approval_url": "https://www.paypal.com/cgi-bin/webscr?cmd=_express-checkout&token=EC-1234567890ABCDEFGHG",
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
          "self": "https://yourdomain.commercelayer.io/api/paypal_payments/xYZkjABcde/relationships/order",
          "related": "https://yourdomain.commercelayer.io/api/paypal_payments/xYZkjABcde/order"
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

