---
description: How to create an adyen gateway via API
---

# Create an adyen gateway

To create a new adyen gateway, send a `POST` request to the `/api/adyen_gateways` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/adyen_gateways**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| attributes.**merchant_account** | `string` | Required |
| attributes.**api_key** | `string` | Required |
| attributes.**live_url_prefix** | `string` | Required |
| relationships.**adyen_payments** | `array` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new adyen gateway:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/adyen_gateways \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "adyen_gateways",
    "attributes": {
      "name": "US payment gateway",
      "merchant_account": "xxxx-yyyy-zzzz",
      "api_key": "xxxx-yyyy-zzzz",
      "live_url_prefix": "1797a841fbb37ca7-AdyenDemo"
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
    "type": "adyen_gateways",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/adyen_gateways/xYZkjABcde"
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
      "live_url_prefix": "1797a841fbb37ca7-AdyenDemo"
    },
    "relationships": {
      "payment_methods": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/adyen_gateways/xYZkjABcde/relationships/payment_methods",
          "related": "https://yourdomain.commercelayer.io/api/adyen_gateways/xYZkjABcde/payment_methods"
        }
      },
      "adyen_payments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/adyen_gateways/xYZkjABcde/relationships/adyen_payments",
          "related": "https://yourdomain.commercelayer.io/api/adyen_gateways/xYZkjABcde/adyen_payments"
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

