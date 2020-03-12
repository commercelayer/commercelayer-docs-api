---
description: How to update an existing customer subscription via API
---

# Update a customer subscription

To update an existing customer subscription, send a `PATCH` request to the `/api/customer_subscriptions/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://yourdomain.commercelayer.io**/api/customer_subscriptions/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the customer subscription identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/customer_subscriptions/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "customer_subscriptions",
    "id": "xYZkjABcde"
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
    "type": "customer_subscriptions",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/customer_subscriptions/xYZkjABcde"
    },
    "attributes": {
      "customer_email": "john@example.com",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "customer": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/customer_subscriptions/xYZkjABcde/relationships/customer",
          "related": "https://yourdomain.commercelayer.io/api/customer_subscriptions/xYZkjABcde/customer"
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

