---
description: How to fetch a specific authorization via API
---

# Retrieve an authorization

To fetch a single authorization, send a `GET` request to the `/api/authorizations/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/authorizations/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the authorization identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/authorizations/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

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
      "token": null,
      "gateway_transaction_id": null,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      },
      "cvv_code": null,
      "cvv_message": null,
      "avs_code": null,
      "avs_message": null,
      "fraud_review": null,
      "capture_amount_cents": "500",
      "capture_amount_float": "5.0",
      "formatted_capture_amount": "€5,00",
      "capture_balance_cents": "1000",
      "capture_balance_float": "10.0",
      "formatted_capture_balance": "€10,00",
      "void_balance_cents": "1500",
      "void_balance_float": "15.0",
      "formatted_void_balance": "€15,00"
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

