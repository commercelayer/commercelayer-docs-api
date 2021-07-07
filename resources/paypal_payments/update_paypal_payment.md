---
description: How to update an existing paypal payment via API
---

# Update a paypal payment

To update an existing paypal payment, send a `PATCH` request to the `/api/paypal_payments/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://yourdomain.commercelayer.io**/api/paypal\_payments/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**paypal\_payer\_id** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**order** | `object` | Optional |

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
      "reference": "ANY-EXTERNAL-REFEFERNCE"
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
      "paypal_payer_id": "ABCDEFGHG123456",
      "name": "ABCDEFGHG123456",
      "paypal_id": "1234567890",
      "status": "created",
      "approval_url": "https://www.paypal.com/cgi-bin/webscr?cmd=_express-checkout&token=EC-1234567890ABCDEFGHG",
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
          "self": "https://yourdomain.commercelayer.io/api/paypal_payments/xYZkjABcde/relationships/order",
          "related": "https://yourdomain.commercelayer.io/api/paypal_payments/xYZkjABcde/order"
        }
      },
      "payment_gateway": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/paypal_payments/xYZkjABcde/relationships/payment_gateway",
          "related": "https://yourdomain.commercelayer.io/api/paypal_payments/xYZkjABcde/payment_gateway"
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

