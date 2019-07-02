---
description: How to create An import via API
---

# Create An import

To create a new import, send a `POST` request to the `/api/imports` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

```text
**POST** https://yourdomain.commercelayer.io**/api/imports**
```

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**resource_type** | `string` | required |
| attributes.**parent_resource_id** | `integer` | required |
| attributes.**status** | `string` |  |
| attributes.**started_at** | `datetime` |  |
| attributes.**completed_at** | `datetime` |  |
| attributes.**inputs** | `object` | required |
| attributes.**errors_count** | `integer` |  |
| attributes.**warnings_count** | `integer` |  |
| attributes.**destroyed_count** | `integer` |  |
| attributes.**errors_log** | `object` |  |
| attributes.**warnings_log** | `object` |  |
| attributes.**cleanup_records** | `boolean` |  |
| attributes.**id** | `string` | required |
| attributes.**created_at** | `datetime` | required |
| attributes.**updated_at** | `datetime` | required |
| attributes.**reference** | `string` | optional |
| attributes.**metadata** | `object` | optional |

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
      "resource_type": "skus"
      "parent_resource_id": "1234"
      "inputs": "[{:code=>"ABC", :name=>"Foo"}, {:code=>"DEF", :name=>"Bar"}]"
    },
    "relationships": {
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `import` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "imports",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/imports/xYZkjABcde"
    },
    "attributes": {
        "resource_type": "skus"
        "parent_resource_id": "1234"
        "status": "started"
        "started_at": "2018-01-01T12:00:00.000Z"
        "completed_at": "2018-01-01T12:00:00.000Z"
        "inputs": "[{:code=>"ABC", :name=>"Foo"}, {:code=>"DEF", :name=>"Bar"}]"
        "errors_count": "3"
        "warnings_count": "1"
        "destroyed_count": "99"
        "errors_log": "[{:"code:ABC"=>{:name=>["has already been taken"]}}]"
        "warnings_log": "[{:"code:ABC"=>["could not be deleted"]}]"
        "cleanup_records": "true"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
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
