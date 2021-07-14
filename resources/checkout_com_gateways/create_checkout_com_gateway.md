---
description: How to create a checkout com gateway via API
---

# Create a checkout com gateway

To create a new checkout com gateway, send a `POST` request to the `/api/checkout_com_gateways` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/checkout_com_gateways**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| attributes.**secret_key** | `string` | Required |
| attributes.**public_key** | `string` | Required |
| relationships.**checkout_com_payments** | `array` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new checkout com gateway:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/checkout_com_gateways \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "checkout_com_gateways",
    "attributes": {
      "name": "US payment gateway",
      "secret_key": "sk_test_xxxx-yyyy-zzzz",
      "public_key": "pk_test_xxxx-yyyy-zzzz"
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
    "type": "checkout_com_gateways",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde"
    },
    "attributes": {
      "name": "US payment gateway",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      },
      "webhook_endpoint_id": "xxxx-yyyy-zzzz",
      "webhook_endpoint_secret": "xxxx-yyyy-zzzz",
      "webhook_endpoint_url": "https://core.commercelayer.co/webhook_callbacks/checkout_com_gateways/xxxxx"
    },
    "relationships": {
      "payment_methods": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde/relationships/payment_methods",
          "related": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde/payment_methods"
        }
      },
      "checkout_com_payments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde/relationships/checkout_com_payments",
          "related": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde/checkout_com_payments"
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

