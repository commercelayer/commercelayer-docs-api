---
description: How to create a customer password reset via API
---

# Create a customer password reset

To create a new customer password reset, send a `POST` request to the `/api/customer_password_resets` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/customer_password_resets**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**customer_email** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new customer password reset:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/customer_password_resets \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "customer_password_resets",
    "attributes": {
      "customer_email": "john@example.com"
    },
    "relationships": {
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `customer password reset` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "customer_password_resets",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/customer_password_resets/xYZkjABcde"
    },
    "attributes": {
        "customer_email": "john@example.com",
        "reset_password_token": "xhFfkmfybsLxzaAP6xcs",
        "reset_password_at": "2018-01-01T12:00:00.000Z",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANYREFEFERNCE",
        "metadata": {
  "foo": "bar"
},
    },
    "relationships": {
        "customer": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/customer_password_resets/xYZkjABcde/relationships/customer",
              "related": "https://yourdomain.commercelayer.io/api/customer_password_resets/xYZkjABcde/customer"
          }
        },
      },
      "meta": {
          "mode": "test"
      }
  }
}
```
{% endtab %}
{% endtabs %}
