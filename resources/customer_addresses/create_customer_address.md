---
description: How to create a customer address via API
---

# Create a customer address

To create a new customer address, send a `POST` request to the `/api/customer_addresses` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/customer_addresses**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**customer** | `object` | Required |
| relationships.**address** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new customer address:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/customer_addresses \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "customer_addresses",
    "attributes": {
    },
    "relationships": {
      "customer": {
        "data": {
          "type": "customers",
          "id": "QWERtyUpBa"
        }
      }
      "address": {
        "data": {
          "type": "addresses",
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
    "type": "customer_addresses",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/customer_addresses/xYZkjABcde"
    },
    "attributes": {
      "name": "John Smith, 2883 Geraldine Lane Apt.23, 10013 New York NY (US) (212) 646-338-1228",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "customer": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/customer_addresses/xYZkjABcde/relationships/customer",
          "related": "https://yourdomain.commercelayer.io/api/customer_addresses/xYZkjABcde/customer"
        }
      },
      "address": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/customer_addresses/xYZkjABcde/relationships/address",
          "related": "https://yourdomain.commercelayer.io/api/customer_addresses/xYZkjABcde/address"
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
