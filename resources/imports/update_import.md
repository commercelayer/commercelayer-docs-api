---
description: How to update an existing import via API
---

# Update an import

To update an existing import, send a `PATCH` request to the `/api/imports/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/imports/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the import identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/imports/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "imports",
    "id": "xYZkjABcde",
    "attributes": {
      "reference": "ANY-EXTERNAL-REFEFERNCE"
    },
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
    "type": "imports",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/imports/xYZkjABcde"
    },
    "attributes": {
      "resource_type": "skus",
      "parent_resource_id": "1234",
      "status": "started",
      "started_at": "2018-01-01T12:00:00.000Z",
      "completed_at": "2018-01-01T12:00:00.000Z",
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
      "errors_count": "3",
      "warnings_count": "1",
      "destroyed_count": "99",
      "errors_log": [
        {
          "code:ABC": {
            "name": [
              "has already been taken"
            ]
          }
        }
      ],
      "warnings_log": [
        {
          "code:ABC": [
            "could not be deleted"
          ]
        }
      ],
      "cleanup_records": "true",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
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
