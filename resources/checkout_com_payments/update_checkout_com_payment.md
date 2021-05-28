---
description: How to update an existing checkout com payment via API
---

# Update a checkout com payment

To update an existing checkout com payment, send a `PATCH` request to the `/api/checkout_com_payments/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://yourdomain.commercelayer.io**/api/checkout\_com\_payments/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**payment\_type** | `string` | Optional |
| attributes.**token** | `string` | Optional |
| attributes.**session\_id** | `string` | Optional |
| attributes.**\_authorize** | `boolean, value is 'true'` | Optional |
| attributes.**\_details** | `boolean, value is 'true'` | Optional |
| attributes.**\_refresh** | `boolean, value is 'true'` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**order** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the checkout com payment identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/checkout_com_payments/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "checkout_com_payments",
    "id": "xYZkjABcde",
    "attributes": {
      "session_id": "sid_y3oqhf46pyzuxjbcn2giaqnb44"
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
  }
}
```
{% endtab %}
{% endtabs %}

