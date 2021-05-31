---
description: How to create a stripe gateway via API
---

# Create a stripe gateway

To create a new stripe gateway, send a `POST` request to the `/api/stripe_gateways` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/stripe_gateways**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| attributes.**login** | `string` | Required |
| attributes.**publishable_key** | `string` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new stripe gateway:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/stripe_gateways \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "stripe_gateways",
    "attributes": {
      "name": "US payment gateway",
      "login": "sk_live_xxxx-yyyy-zzzz"
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
    "type": "stripe_gateways",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/stripe_gateways/xYZkjABcde"
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
      "webhook_endpoint_url": "https://core.commercelayer.co/webhook_callbacks/stripe_gateways/xxxxx"
    },
    "relationships": {
      "payment_methods": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stripe_gateways/xYZkjABcde/relationships/payment_methods",
          "related": "https://yourdomain.commercelayer.io/api/stripe_gateways/xYZkjABcde/payment_methods"
        }
      },
      "stripe_payments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stripe_gateways/xYZkjABcde/relationships/stripe_payments",
          "related": "https://yourdomain.commercelayer.io/api/stripe_gateways/xYZkjABcde/stripe_payments"
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

