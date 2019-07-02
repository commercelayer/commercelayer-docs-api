---
description: How to create A paypal payment via API
---

# Create A paypal payment

To create a new paypal payment, send a `POST` request to the `/api/paypal_payments` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https\://yourdomain.commercelayer.io**/api/paypal_payments**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**return_url** | `string` | required |
| attributes.**cancel_url** | `string` | required |
| attributes.**note_to_payer** | `string` | optional |
| attributes.**paypal_payer_id** | `string` |  |
| attributes.**name** | `string` |  |
| attributes.**paypal_id** | `string` |  |
| attributes.**status** | `string` |  |
| attributes.**approval_url** | `string` |  |
| attributes.**id** | `string` | required |
| attributes.**created_at** | `datetime` | required |
| attributes.**updated_at** | `datetime` | required |
| attributes.**reference** | `string` | optional |
| attributes.**metadata** | `object` | optional |
| relationships.**order** | `has_one` | required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new paypal payment:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/paypal_payments \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "paypal_payments",
    "attributes": {
      "return_url": "https://yourbrand.com/thankyou"
      "cancel_url": "https://yourbrand.com/checkout/payment"
    },
    "relationships": {
      "order": {
        "data": {
          "type": "orders",
          "id": "zxcVBnMASd"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `paypal payment` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "paypal_payments",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/paypal_payments/xYZkjABcde"
    },
    "attributes": {
        "return_url": "https://yourbrand.com/thankyou"
        "cancel_url": "https://yourbrand.com/checkout/payment"
        "note_to_payer": "Thank you for shopping with us!"
        "paypal_payer_id": "ABCDEFG123456"
        "name": "ABCDEFG123456"
        "paypal_id": "1234567890"
        "status": "created"
        "approval_url": "https://www.paypal.com/cgi-bin/webscr?cmd=_express-checkout&token=EC-1234567890ABCDEFG"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
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