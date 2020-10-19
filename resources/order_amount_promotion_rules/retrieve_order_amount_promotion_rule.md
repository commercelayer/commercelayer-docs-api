---
description: How to fetch a specific order amount promotion rule via API
---

# Retrieve an order amount promotion rule

To fetch a single order amount promotion rule, send a `GET` request to the `/api/order_amount_promotion_rules/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/order_amount_promotion_rules/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the order amount promotion rule identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/order_amount_promotion_rules/xYZkjABcde \
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
      "order_amount_cents": "1000",
      "order_amount_float": "10.0",
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

