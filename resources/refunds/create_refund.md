---
description: How to create a refund via API
---

# Create a refund

To create a new refund, send a `POST` request to the `/api/refunds` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/refunds**

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
The following request creates a new refund:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/refunds \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "refunds"
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
    "type": "refunds",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/refunds/xYZkjABcde"
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
          "self": "https://yourdomain.commercelayer.io/api/refunds/xYZkjABcde/relationships/order",
          "related": "https://yourdomain.commercelayer.io/api/refunds/xYZkjABcde/order"
        }
      },
      "reference_capture": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/refunds/xYZkjABcde/relationships/reference_capture",
          "related": "https://yourdomain.commercelayer.io/api/refunds/xYZkjABcde/reference_capture"
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

