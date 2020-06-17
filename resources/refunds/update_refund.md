---
description: How to update an existing refund via API
---

# Update a refund

To update an existing refund, send a `PATCH` request to the `/api/refunds/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/refunds/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the refund identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/refunds/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "refunds",
    "id": "xYZkjABcde",
    "attributes": {
      "reference": "ANY-EXTERNAL-REFEFERNCE"
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

