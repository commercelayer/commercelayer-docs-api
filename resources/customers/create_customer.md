---
description: How to create a customer via API
---

# Create a customer

To create a new customer, send a `POST` request to the `/api/customers` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/customers**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**email** | `string` | Required |
| attributes.**password** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**customer_group** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new customer:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/customers \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "customers",
    "attributes": {
      "email": "john@example.com"
    },
    "relationships": {
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `customer` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "customers",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde"
    },
    "attributes": {
        "email": "john@example.com"
        "status": "prospect"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
        "customer_group": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/relationships/customer_group",
              "related": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/customer_group"
          }
        }
        "customer_addresses": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/relationships/customer_addresses",
              "related": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/customer_addresses"
          }
        }
        "customer_payment_sources": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/relationships/customer_payment_sources",
              "related": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/customer_payment_sources"
          }
        }
        "customer_subscriptions": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/relationships/customer_subscriptions",
              "related": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/customer_subscriptions"
          }
        }
        "orders": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/relationships/orders",
              "related": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/orders"
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
