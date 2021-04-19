---
description: How to update an existing in stock subscription via API
---

# Update an in stock subscription

To update an existing in stock subscription, send a `PATCH` request to the `/api/in_stock_subscriptions/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/in_stock_subscriptions/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**sku_code** | `string` | Optional |
| attributes.**_activate** | `boolean, value is 'true'` | Optional |
| attributes.**_deactivate** | `boolean, value is 'true'` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**market** | `object` | Optional |
| relationships.**customer** | `object` | Optional |
| relationships.**sku** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the in stock subscription identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/in_stock_subscriptions/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "in_stock_subscriptions",
    "id": "xYZkjABcde",
    "attributes": {
      "sku_code": "TSHIRTMM000000FFFFFFXLXX"
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

