---
description: How to update an existing paypal payment via API
---

# Update a paypal payment

To update an existing paypal payment, send a `PATCH` request to the `/api/paypal_payments/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/paypal_payments/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**paypal_payer_id** | `string` |  |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**order** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the paypal payment identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/paypal_payments/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "paypal_payments",
    "id": "xYZkjABcde",
    "attributes": {
      "paypal_payer_id": "ABCDEFG123456"
      "reference": "ANYREFEFERNCE"
      "metadata": "{:foo=>"bar"}"
    },
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
On success, the API responds with a `200 OK` status code, returning the updated resource object:

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
