---
description: How to update an existing customer via API
---

# Update a customer

To update an existing customer, send a `PATCH` request to the `/api/customers/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/customers/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**email** | `string` | Required |
| attributes.**password** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**customer_group** | `object` | Optional |

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
      "email": "john@example.com"
      "password": "secret"
      "reference": "ANYREFEFERNCE"
      "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
      "customer_group": {
        "data": {
          "type": "customer_groups",
          "id": "QWERtyUpBa"
        }
      }
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
    "id": "{{customer_id}}",
    "type": "customers",
    "links": {
      "self": "https://{{subdomain}}.commercelayer.io/api/customers/{{customer_id}}"
    },
    "attributes": {
      "email": "john@example.com",
      "status": "prospect",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "customer_group": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/customers/{{customer_id}}/relationships/customer_group",
          "related": "https://{{subdomain}}.commercelayer.io/api/customers/{{customer_id}}/customer_group"
        }
      },
      "customer_addresses": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/customers/{{customer_id}}/relationships/customer_addresses",
          "related": "https://{{subdomain}}.commercelayer.io/api/customers/{{customer_id}}/customer_addresses"
        }
      },
      "customer_payment_sources": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/customers/{{customer_id}}/relationships/customer_payment_sources",
          "related": "https://{{subdomain}}.commercelayer.io/api/customers/{{customer_id}}/customer_payment_sources"
        }
      },
      "customer_subscriptions": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/customers/{{customer_id}}/relationships/customer_subscriptions",
          "related": "https://{{subdomain}}.commercelayer.io/api/customers/{{customer_id}}/customer_subscriptions"
        }
      },
      "orders": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/customers/{{customer_id}}/relationships/orders",
          "related": "https://{{subdomain}}.commercelayer.io/api/customers/{{customer_id}}/orders"
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
