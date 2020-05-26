---
description: How to create an in stock subscription via API
---

# Create an in stock subscription

To create a new in stock subscription, send a `POST` request to the `/api/in_stock_subscriptions` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/in_stock_subscriptions**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**customer_email** | `string` | Optional |
| attributes.**sku_code** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**market** | `object` | Required |
| relationships.**customer** | `object` | Required |
| relationships.**sku** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new in stock subscription:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/in_stock_subscriptions \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "in_stock_subscriptions",
    "relationships": {
      "market": {
        "data": {
          "type": "markets",
          "id": "QWERtyUpBa"
        }
      },
      "customer": {
        "data": {
          "type": "customers",
          "id": "QWERtyUpBa"
        }
      },
      "sku": {
        "data": {
          "type": "skus",
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

