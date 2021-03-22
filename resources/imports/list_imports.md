---
description: How to fetch a collection of imports via API
---

# List all imports

To fetch a collection of imports, send a `GET` request to the `/api/imports` endpoint.

## Request

**GET** https://yourdomain.commercelayer.io**/api/imports**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of imports:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/imports/ \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a paginated collection of resource objects:

```javascript
{
  "data": [
    {
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
        "errors_count": 3,
        "warnings_count": 1,
        "destroyed_count": 99,
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
    },
    {
      "other": "... 9 imports (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/imports?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/imports?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/imports?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

### Sortable attributes

The list of imports can be sorted by the following attributes:

* `resource_type`
* `parent_resource_id`
* `status`
* `started_at`
* `completed_at`
* `errors_count`
* `warnings_count`
* `destroyed_count`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

