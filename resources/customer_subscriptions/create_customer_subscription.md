---
description: How to create A customer subscription via API
---

# Create A customer subscription

To create a new customer subscription, send a `POST` request to the `/api/customer_subscriptions` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain.commercelayer.io**/api/customer_subscriptions**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**customer_email** | `string` | required |
| attributes.**id** | `string` | required |
| attributes.**created_at** | `datetime` | required |
| attributes.**updated_at** | `datetime` | required |
| attributes.**reference** | `string` | optional |
| attributes.**metadata** | `object` | optional |
| relationships.**customer** | `has_one` |  |

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
        "customer_email": ""
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
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
