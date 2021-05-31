---
description: How to fetch a specific customer via API
---

# Retrieve a customer

To fetch a single customer, send a `GET` request to the `/api/customers/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/customers/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the customer identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/customers/xYZkjABcde \
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
    "type": "customers",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde"
    },
    "attributes": {
      "email": "john@example.com",
      "status": "prospect",
      "has_password": true,
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
      },
      "returns": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/relationships/returns",
          "related": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/returns"
        }
      },
      "attachments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/relationships/attachments",
          "related": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/attachments"
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

