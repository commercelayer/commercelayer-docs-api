---
description: How to fetch a specific refund via API
---

# Retrieve a refund

To fetch a single refund, send a `GET` request to the `/api/refunds/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/refunds/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the refund identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/refunds/xYZkjABcde \
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
    "type": "refunds",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/refunds/xYZkjABcde"
    },
    "attributes": {
      "number": null,
      "currency_code": "EUR",
      "amount_cents": 1500,
      "amount_float": 15.0,
      "formatted_amount": "€15,00",
      "succeeded": false,
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

