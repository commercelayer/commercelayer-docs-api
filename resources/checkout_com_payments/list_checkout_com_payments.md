---
description: How to fetch a collection of checkout com payments via API
---

# List all checkout com payments

To fetch a collection of checkout com payments, send a `GET` request to the `/api/checkout_com_payments` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/checkout_com_payments**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of checkout com payments:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/checkout_com_payments/ \
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
      "type": "checkout_com_payments",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/checkout_com_payments/xYZkjABcde"
      },
      "attributes": {
        "payment_type": "token",
        "token": "tok_4gzeau5o2uqubbk6fufs3m7p54",
        "session_id": "sid_y3oqhf46pyzuxjbcn2giaqnb44",
        "source_id": "src_nwd3m4in3hkuddfpjsaevunhdy",
        "customer_token": "cus_udst2tfldj6upmye2reztkmm4i",
        "redirect_uri": "https://api.checkout.com/3ds/pay_mbabizu24mvu3mela5njyhpit4",
        "payment_response": "See Checkout.com official documentation",
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
            "self": "https://yourdomain.commercelayer.io/api/checkout_com_payments/xYZkjABcde/relationships/order",
            "related": "https://yourdomain.commercelayer.io/api/checkout_com_payments/xYZkjABcde/order"
          }
        },
        "payment_gateway": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/checkout_com_payments/xYZkjABcde/relationships/payment_gateway",
            "related": "https://yourdomain.commercelayer.io/api/checkout_com_payments/xYZkjABcde/payment_gateway"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 checkout_com_payments (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/checkout_com_payments?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/checkout_com_payments?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/checkout_com_payments?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of checkout com payments can be sorted by the following attributes:

* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

