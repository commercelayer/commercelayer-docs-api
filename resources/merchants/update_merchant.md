---
description: How to update an existing merchant via API
---

# Update a merchant

To update an existing merchant, send a `PATCH` request to the `/api/merchants/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/merchants/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**address** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the merchant identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/merchants/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "merchants",
    "id": "xYZkjABcde",
    "attributes": {
      "name": "The Brand Inc."
    },
    "relationships": {
      "address": {
        "data": {
          "type": "addresses",
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
    "type": "merchants",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/merchants/xYZkjABcde"
    },
    "attributes": {
      "name": "The Brand Inc.",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "address": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/merchants/xYZkjABcde/relationships/address",
          "related": "https://yourdomain.commercelayer.io/api/merchants/xYZkjABcde/address"
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
