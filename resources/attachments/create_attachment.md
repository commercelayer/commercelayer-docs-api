---
description: How to create an attachment via API
---

# Create an attachment

To create a new attachment, send a `POST` request to the `/api/attachments` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain.commercelayer.io**/api/attachments**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**description** | `string` | Optional |
| attributes.**url** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**attachable** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new attachment:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/attachments \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "attachments",
    "attributes": {
      "name": "DDT transport document"
    },
    "relationships": {
      "attachable": {
        "data": {
          "type": "attachables",
          "id": "QWERtyUpBa"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `attachment` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "attachments",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/attachments/xYZkjABcde"
    },
    "attributes": {
        "name": "DDT transport document",
        "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        "url": "https://s3.yourbrand.com/attachment.pdf",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANYREFEFERNCE",
        "metadata": {
  "foo": "bar"
},
    },
    "relationships": {
        "attachable": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/attachments/xYZkjABcde/relationships/attachable",
              "related": "https://yourdomain.commercelayer.io/api/attachments/xYZkjABcde/attachable"
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

