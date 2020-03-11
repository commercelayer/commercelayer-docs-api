---
description: How to create a webhook via API
---

# Create a webhook

To create a new webhook, send a `POST` request to the `/api/webhooks` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/webhooks**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**topic** | `string` | Required |
| attributes.**callback_url** | `string` | Required |
| attributes.**include_resources** | `array` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new webhook:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/webhooks \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "webhooks",
    "attributes": {
      "topic": "orders.place",
      "callback_url": "https://yourapp.com/webhooks"
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
    "type": "webhooks",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/webhooks/xYZkjABcde"
    },
    "attributes": {
      "topic": "orders.place",
      "callback_url": "https://yourapp.com/webhooks",
      "include_resources": "[customer, shipping_address, billing_address]",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
    },
    "meta": {
      "mode": "test"
    }
  }
}
```
{% endtab %}
{% endtabs %}
