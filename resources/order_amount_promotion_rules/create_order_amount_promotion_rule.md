---
description: How to create an order amount promotion rule via API
---

# Create an order amount promotion rule

To create a new order amount promotion rule, send a `POST` request to the `/api/order_amount_promotion_rules` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain.commercelayer.io**/api/order\_amount\_promotion\_rules**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| attributes.**order\_amount\_cents** | `integer` | Optional |
| relationships.**promotion** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new order amount promotion rule:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/order_amount_promotion_rules \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "order_amount_promotion_rules",
    "relationships": {
      "promotion": {
        "data": {
          "type": "promotions",
          "id": "QWERtyUpBa"
        }
      }
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
    "type": "order_amount_promotion_rules",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/order_amount_promotion_rules/xYZkjABcde"
    },
    "attributes": {
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      },
      "order_amount_cents": 1000,
      "order_amount_float": 10.0,
      "formatted_order_amount": "€10,00"
    },
    "relationships": {
      "promotion": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/order_amount_promotion_rules/xYZkjABcde/relationships/promotion",
          "related": "https://yourdomain.commercelayer.io/api/order_amount_promotion_rules/xYZkjABcde/promotion"
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

