---
description: How to create an authorization via API
---

# Create an authorization

To create a new authorization, send a `POST` request to the `/api/authorizations` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/authorizations**

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
The following request creates a new authorization:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/authorizations \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "authorizations"
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
    "type": "authorizations",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/authorizations/xYZkjABcde"
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
      "cvv_code": null,
      "cvv_message": null,
      "avs_code": null,
      "avs_message": null,
      "fraud_review": null,
      "token": null,
      "gateway_transaction_id": null,
      "capture_amount_cents": "500",
      "capture_amount_float": "5.0",
      "formatted_capture_amount": "€5,00",
      "capture_balance_cents": "1000",
      "capture_balance_float": "10.0",
      "formatted_capture_balance": "€10,00",
      "void_balance_cents": "1500",
      "void_balance_float": "15.0",
      "formatted_void_balance": "€15,00",
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
          "self": "https://yourdomain.commercelayer.io/api/authorizations/xYZkjABcde/relationships/order",
          "related": "https://yourdomain.commercelayer.io/api/authorizations/xYZkjABcde/order"
        }
      },
      "captures": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/authorizations/xYZkjABcde/relationships/captures",
          "related": "https://yourdomain.commercelayer.io/api/authorizations/xYZkjABcde/captures"
        }
      },
      "voids": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/authorizations/xYZkjABcde/relationships/voids",
          "related": "https://yourdomain.commercelayer.io/api/authorizations/xYZkjABcde/voids"
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

