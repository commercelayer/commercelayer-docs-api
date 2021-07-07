---
description: How to fetch a specific gift card recipient via API
---

# Retrieve a gift card recipient

To fetch a single gift card recipient, send a `GET` request to the `/api/gift_card_recipients/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/gift\_card\_recipients/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the gift card recipient identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/gift_card_recipients/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

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

