---
description: How to create an import via API
---

# Create an import

To create a new import, send a `POST` request to the `/api/imports` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain.commercelayer.io**/api/imports**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**resource\_type** | `string` | Required |
| attributes.**parent\_resource\_id** | `string` | Required |
| attributes.**inputs** | `array` | Required |
| attributes.**cleanup\_records** | `boolean` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new import:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/imports \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "imports",
    "attributes": {
      "resource_type": "skus",
      "parent_resource_id": "1234",
      "inputs": [
        {
          "code": "ABC",
          "name": "Foo"
        },
        {
          "code": "DEF",
          "name": "Bar"
        }
      ]
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
    "type": "imports",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/imports/xYZkjABcde"
    },
    "attributes": {
      "resource_type": "skus",
      "parent_resource_id": "1234",
      "status": "in_progress",
      "started_at": "2018-01-01T12:00:00.000Z",
      "completed_at": "2018-01-01T12:00:00.000Z",
      "interrupted_at": "2018-01-01T12:00:00.000Z",
      "inputs": [
        {
          "code": "ABC",
          "name": "Foo"
        },
        {
          "code": "DEF",
          "name": "Bar"
        }
      ],
      "inputs_size": 300,
      "errors_count": 30,
      "warnings_count": 1,
      "destroyed_count": 99,
      "processed_count": 270,
      "errors_log": [
        {
          "ABC": {
            "name": [
              "has already been taken"
            ]
          }
        }
      ],
      "warnings_log": [
        {
          "ABC": [
            "could not be deleted"
          ]
        }
      ],
      "cleanup_records": true,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {},
    "meta": {
      "mode": "test"
    }
  }
}
```
{% endtab %}
{% endtabs %}

