---
description: How to fetch a specific in stock subscription via API
---

# Retrieve an in stock subscription

To fetch a single in stock subscription, send a `GET` request to the `/api/in_stock_subscriptions/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/in\_stock\_subscriptions/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the in stock subscription identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/in_stock_subscriptions/xYZkjABcde \
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
    "type": "in_stock_subscriptions",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/in_stock_subscriptions/xYZkjABcde"
    },
    "attributes": {
      "status": "active",
      "customer_email": "john@example.com",
      "sku_code": "TSHIRTMM000000FFFFFFXLXX",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "market": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/in_stock_subscriptions/xYZkjABcde/relationships/market",
          "related": "https://yourdomain.commercelayer.io/api/in_stock_subscriptions/xYZkjABcde/market"
        }
      },
      "customer": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/in_stock_subscriptions/xYZkjABcde/relationships/customer",
          "related": "https://yourdomain.commercelayer.io/api/in_stock_subscriptions/xYZkjABcde/customer"
        }
      },
      "sku": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/in_stock_subscriptions/xYZkjABcde/relationships/sku",
          "related": "https://yourdomain.commercelayer.io/api/in_stock_subscriptions/xYZkjABcde/sku"
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

