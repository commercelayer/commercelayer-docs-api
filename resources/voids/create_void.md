---
description: How to create a void via API
---

# Create a void

To create a new void, send a `POST` request to the `/api/voids` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/voids**

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
The following request creates a new void:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/voids \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "voids"
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
    "type": "voids",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/voids/xYZkjABcde"
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
          "self": "https://yourdomain.commercelayer.io/api/voids/xYZkjABcde/relationships/order",
          "related": "https://yourdomain.commercelayer.io/api/voids/xYZkjABcde/order"
        }
      },
      "reference_authorization": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/voids/xYZkjABcde/relationships/reference_authorization",
          "related": "https://yourdomain.commercelayer.io/api/voids/xYZkjABcde/reference_authorization"
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

