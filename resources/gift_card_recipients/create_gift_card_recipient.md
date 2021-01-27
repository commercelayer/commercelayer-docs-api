---
description: How to create a gift card recipient via API
---

# Create a gift card recipient

To create a new gift card recipient, send a `POST` request to the `/api/gift_card_recipients` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/gift_card_recipients**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**email** | `string` | Required |
| attributes.**first_name** | `string` | Optional |
| attributes.**last_name** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**customer** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new gift card recipient:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/gift_card_recipients \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "gift_card_recipients",
    "attributes": {
      "email": "john@example.com"
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
    "type": "gift_card_recipients",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/gift_card_recipients/xYZkjABcde"
    },
    "attributes": {
      "email": "john@example.com",
      "first_name": "John",
      "last_name": "Smith",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
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
          "self": "https://yourdomain.commercelayer.io/api/gift_card_recipients/xYZkjABcde/relationships/customer",
          "related": "https://yourdomain.commercelayer.io/api/gift_card_recipients/xYZkjABcde/customer"
        }
      },
      "attachments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/gift_card_recipients/xYZkjABcde/relationships/attachments",
          "related": "https://yourdomain.commercelayer.io/api/gift_card_recipients/xYZkjABcde/attachments"
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

