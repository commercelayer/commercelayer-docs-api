---
description: How to update an existing customer payment source via API
---

# Update a customer payment source

To update an existing customer payment source, send a `PATCH` request to the `/api/customer_payment_sources/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/customer_payment_sources/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**customer** | `object` | Required |
| relationships.**payment_source** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the customer payment source identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/customer_payment_sources/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "customer_payment_sources",
    "id": "xYZkjABcde",
    "attributes": {
    },
    "relationships": {
      "customer": {
        "data": {
          "type": "customers",
          "id": "QWERtyUpBa"
        }
      },
      "payment_source": {
        "data": {
          "type": "payment_sources",
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
    "type": "customer_payment_sources",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/customer_payment_sources/xYZkjABcde"
    },
    "attributes": {
      "name": "XXXX-XXXX-XXXX-1111",
      "customer_token": "cus_xxxyyyzzz",
      "payment_source_token": "pm_xxxyyyzzz",
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
          "self": "https://yourdomain.commercelayer.io/api/customer_payment_sources/xYZkjABcde/relationships/customer",
          "related": "https://yourdomain.commercelayer.io/api/customer_payment_sources/xYZkjABcde/customer"
        }
      },
      "payment_source": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/customer_payment_sources/xYZkjABcde/relationships/payment_source",
          "related": "https://yourdomain.commercelayer.io/api/customer_payment_sources/xYZkjABcde/payment_source"
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
