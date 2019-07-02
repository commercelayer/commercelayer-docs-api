---
description: How to create A wire transfer via API
---

# Create A wire transfer

To create a new wire transfer, send a `POST` request to the `/api/wire_transfers` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/wire_transfers**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**id** | `string` | required |
| attributes.**created_at** | `datetime` | required |
| attributes.**updated_at** | `datetime` | required |
| attributes.**reference** | `string` | optional |
| attributes.**metadata** | `object` | optional |
| relationships.**order** | `has_one` | required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new wire transfer:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/wire_transfers \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "wire_transfers",
    "attributes": {
    },
    "relationships": {
      "order": {
        "data": {
          "type": "orders",
          "id": "zxcVBnMASd"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `wire transfer` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "wire_transfers",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/wire_transfers/xYZkjABcde"
    },
    "attributes": {
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
        "order": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/wire_transfers/xYZkjABcde/relationships/order",
              "related": "https://yourdomain.commercelayer.io/api/wire_transfers/xYZkjABcde/order"
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
