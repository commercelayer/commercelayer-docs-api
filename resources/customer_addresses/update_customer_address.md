---
description: How to update an existing customer address via API
---

# Update a customer address

To update an existing customer address, send a `PATCH` request to the `/api/customer_addresses/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/customer_addresses/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**customer** | `object` | Required |
| relationships.**address** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the customer address identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/customer_addresses/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "customer_addresses",
    "id": "xYZkjABcde",
    "relationships": {
      "customer": {
        "data": {
          "type": "customers",
          "id": "QWERtyUpBa"
        }
      },
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
On success, the API responds with a `200 OK` status code, returning the updated resource object:

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
      "reference": "ANY-EXTERNAL-REFEFERNCE",
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
