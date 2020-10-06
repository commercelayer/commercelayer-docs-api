---
description: How to update an existing customer via API
---

# Update a customer

To update an existing customer, send a `PATCH` request to the `/api/customers/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://yourdomain.commercelayer.io**/api/customers/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**email** | `string` | Optional |
| attributes.**password** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**customer\_group** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the customer identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/customers/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "customers",
    "id": "xYZkjABcde",
    "attributes": {
      "password": "secret"
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
    "type": "customers",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde"
    },
    "attributes": {
      "email": "john@example.com",
      "status": "prospect",
      "has_password": "true",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "customer_group": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/relationships/customer_group",
          "related": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/customer_group"
        }
      },
      "customer_addresses": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/relationships/customer_addresses",
          "related": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/customer_addresses"
        }
      },
      "customer_payment_sources": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/relationships/customer_payment_sources",
          "related": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/customer_payment_sources"
        }
      },
      "customer_subscriptions": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/relationships/customer_subscriptions",
          "related": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/customer_subscriptions"
        }
      },
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

