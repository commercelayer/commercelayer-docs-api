---
description: How to update an existing authorization via API
---

# Update an authorization

To update an existing authorization, send a `PATCH` request to the `/api/authorizations/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/authorizations/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**_capture** | `boolean, value is 'true'` | Optional |
| attributes.**_capture_amount_cents** | `integer` | Optional |
| attributes.**_void** | `boolean, value is 'true'` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the authorization identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/authorizations/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "authorizations",
    "id": "xYZkjABcde",
    "attributes": {
      "_capture": "true",
      "_capture_amount_cents": "500"
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

