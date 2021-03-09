---
description: How to create an external gateway via API
---

# Create an external gateway

To create a new external gateway, send a `POST` request to the `/api/external_gateways` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/external_gateways**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| attributes.**authorize_url** | `string` | Optional |
| attributes.**capture_url** | `string` | Optional |
| attributes.**void_url** | `string` | Optional |
| attributes.**refund_url** | `string` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new external gateway:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/external_gateways \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "external_gateways",
    "attributes": {
      "name": "US payment gateway"
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
    "type": "external_gateways",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/external_gateways/xYZkjABcde"
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
      "shared_secret": "xxxx-yyyy-zzzz",
      "authorize_url": "https://external_gateway.com/authorize",
      "capture_url": "https://external_gateway.com/capture",
      "void_url": "https://external_gateway.com/void",
      "refund_url": "https://external_gateway.com/refund"
    },
    "relationships": {
      "payment_methods": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/external_gateways/xYZkjABcde/relationships/payment_methods",
          "related": "https://yourdomain.commercelayer.io/api/external_gateways/xYZkjABcde/payment_methods"
        }
      },
      "external_payments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/external_gateways/xYZkjABcde/relationships/external_payments",
          "related": "https://yourdomain.commercelayer.io/api/external_gateways/xYZkjABcde/external_payments"
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

