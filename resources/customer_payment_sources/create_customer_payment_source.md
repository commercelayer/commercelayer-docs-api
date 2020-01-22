---
description: How to create a customer payment source via API
---

# Create a customer payment source

To create a new customer payment source, send a `POST` request to the `/api/customer_payment_sources` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/customer_payment_sources**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**customer** | `object` | Required |
| relationships.**payment_source** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new customer payment source:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/customer_payment_sources \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "customer_payment_sources",
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
On success, the API responds with a `201 Created` status code, returning the created resource object:

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
