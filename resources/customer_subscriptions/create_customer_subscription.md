---
description: How to create a customer subscription via API
---

# Create a customer subscription

To create a new customer subscription, send a `POST` request to the `/api/customer_subscriptions` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain.commercelayer.io**/api/customer\_subscriptions**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**customer\_email** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new customer subscription:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/customer_subscriptions \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "customer_subscriptions",
    "attributes": {
      "customer_email": ""
    },
    "relationships": {
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `customer subscription` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "customer_subscriptions",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/customer_subscriptions/xYZkjABcde"
    },
    "attributes": {
      "customer_email": null,
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
          "self": "https://{{subdomain}}.commercelayer.io/api/customer_subscriptions/{{customer_subscription_id}}/relationships/customer",
          "related": "https://{{subdomain}}.commercelayer.io/api/customer_subscriptions/{{customer_subscription_id}}/customer"
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

