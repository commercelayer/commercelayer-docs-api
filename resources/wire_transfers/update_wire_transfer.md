---
description: How to update an existing wire transfer via API
---

# Update a wire transfer

To update an existing wire transfer, send a `PATCH` request to the `/api/wire_transfers/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/wire_transfers/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**order** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the wire transfer identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/wire_transfers/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "wire_transfers",
    "id": "xYZkjABcde",
    "attributes": {
      "reference": "ANYREFEFERNCE"
      "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
      "order": {
        "data": {
          "type": "orders",
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
    "type": "wire_transfers",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/wire_transfers/xYZkjABcde"
    },
    "attributes": {
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANYREFEFERNCE",
        "metadata": {
  "foo": "bar"
},
    },
    "relationships": {
        "order": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/wire_transfers/xYZkjABcde/relationships/order",
              "related": "https://yourdomain.commercelayer.io/api/wire_transfers/xYZkjABcde/order"
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
