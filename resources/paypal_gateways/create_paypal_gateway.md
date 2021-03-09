---
description: How to create a paypal gateway via API
---

# Create a paypal gateway

To create a new paypal gateway, send a `POST` request to the `/api/paypal_gateways` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/paypal_gateways**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| attributes.**client_id** | `string` | Required |
| attributes.**client_secret** | `string` | Required |
| attributes.**mode** | `string` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new paypal gateway:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/paypal_gateways \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "paypal_gateways",
    "attributes": {
      "name": "US payment gateway",
      "client_id": "xxxx-yyyy-zzzz",
      "client_secret": "xxxx-yyyy-zzzz",
      "mode": "live"
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
    "type": "paypal_gateways",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/paypal_gateways/xYZkjABcde"
    },
    "attributes": {
      "name": "US payment gateway",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "payment_methods": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/paypal_gateways/xYZkjABcde/relationships/payment_methods",
          "related": "https://yourdomain.commercelayer.io/api/paypal_gateways/xYZkjABcde/payment_methods"
        }
      },
      "paypal_payments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/paypal_gateways/xYZkjABcde/relationships/paypal_payments",
          "related": "https://yourdomain.commercelayer.io/api/paypal_gateways/xYZkjABcde/paypal_payments"
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

