---
description: How to create a capture via API
---

# Create a capture

To create a new capture, send a `POST` request to the `/api/captures` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/captures**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new capture:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/captures \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "captures"
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
    "type": "captures",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/captures/xYZkjABcde"
    },
    "attributes": {
      "number": null,
      "currency_code": "EUR",
      "amount_cents": "1500",
      "amount_float": "15.0",
      "formatted_amount": "€15,00",
      "succeeded": "false",
      "message": null,
      "error_code": null,
      "error_detail": null,
      "token": null,
      "gateway_transaction_id": null,
      "refund_amount_cents": "500",
      "refund_amount_float": "5.0",
      "formatted_refund_amount": "€5,00",
      "refund_balance_cents": "1000",
      "refund_balance_float": "10.0",
      "formatted_refund_balance": "€10,00",
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
          "self": "https://yourdomain.commercelayer.io/api/captures/xYZkjABcde/relationships/order",
          "related": "https://yourdomain.commercelayer.io/api/captures/xYZkjABcde/order"
        }
      },
      "reference_authorization": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/captures/xYZkjABcde/relationships/reference_authorization",
          "related": "https://yourdomain.commercelayer.io/api/captures/xYZkjABcde/reference_authorization"
        }
      },
      "refunds": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/captures/xYZkjABcde/relationships/refunds",
          "related": "https://yourdomain.commercelayer.io/api/captures/xYZkjABcde/refunds"
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

