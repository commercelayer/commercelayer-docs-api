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
  "id": "{{paypal_payment_id}}",
  "type": "paypal_payments",
  "links": {
    "self": "https://{{subdomain}}.commercelayer.io/api/paypal_payments/{{paypal_payment_id}}"
  },
  "attributes": {
    "return_url": "https://yourbrand.com/thankyou",
    "cancel_url": "https://yourbrand.com/checkout/payment",
    "note_to_payer": "Thank you for shopping with us!",
    "paypal_payer_id": "ABCDEFG123456",
    "name": "ABCDEFG123456",
    "paypal_id": "1234567890",
    "status": "created",
    "approval_url": "https://www.paypal.com/cgi-bin/webscr?cmd=_express-checkout&token=EC-1234567890ABCDEFG",
    "created_at": "2018-01-01T12:00:00.000Z",
    "updated_at": "2018-01-01T12:00:00.000Z",
    "reference": "ANYREFEFERNCE",
    "metadata": {
      "foo": "bar"
    }
  },
  "relationships": {
    "order": {
      "links": {
        "self": "https://{{subdomain}}.commercelayer.io/api/paypal_payments/{{paypal_payment_id}}/relationships/order",
        "related": "https://{{subdomain}}.commercelayer.io/api/paypal_payments/{{paypal_payment_id}}/order"
      }
    }
  },
  "meta": {
    "mode": "test"
  }
}
```
{% endtab %}
{% endtabs %}

