---
description: How to update an existing customer password reset via API
---

# Update a customer password reset

To update an existing customer password reset, send a `PATCH` request to the `/api/customer_password_resets/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://yourdomain.commercelayer.io**/api/customer\_password\_resets/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**customer\_password** | `string` | Optional |
| attributes.**\_reset\_password\_token** | `string` |  |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the customer password reset identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/customer_password_resets/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "customer_password_resets",
    "id": "xYZkjABcde",
    "attributes": {
      "customer_password": "secret"
      "_reset_password_token": "xhFfkmfybsLxzaAP6xcs"
      "reference": "ANYREFEFERNCE"
      "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
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
    "type": "customer_password_resets",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/customer_password_resets/xYZkjABcde"
    },
    "attributes": {
        "customer_email": "john@example.com"
        "reset_password_token": "xhFfkmfybsLxzaAP6xcs"
        "reset_password_at": "2018-01-01T12:00:00.000Z"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
        "customer": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/customer_password_resets/xYZkjABcde/relationships/customer",
              "related": "https://yourdomain.commercelayer.io/api/customer_password_resets/xYZkjABcde/customer"
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

