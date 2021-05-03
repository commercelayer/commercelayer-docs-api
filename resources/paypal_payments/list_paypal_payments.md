---
description: How to fetch a collection of paypal payments via API
---

# List all paypal payments

To fetch a collection of paypal payments, send a `GET` request to the `/api/paypal_payments` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/paypal\_payments**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of paypal payments:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/paypal_payments/ \
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
    },
    {
      "other": "... 9 paypal_payments (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/paypal_payments?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/paypal_payments?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/paypal_payments?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of paypal payments can be sorted by the following attributes:

* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

