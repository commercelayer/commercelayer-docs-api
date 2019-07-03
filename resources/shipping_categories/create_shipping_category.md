---
description: How to create a shipping category via API
---

# Create a shipping category

To create a new shipping category, send a `POST` request to the `/api/shipping_categories` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/shipping_categories**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new shipping category:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/shipping_categories \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "shipping_categories",
    "attributes": {
      "name": "Merchandise"
    },
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
    "type": "shipping_categories",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/shipping_categories/xYZkjABcde"
    },
    "attributes": {
      "name": "Merchandise",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "skus": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipping_categories/xYZkjABcde/relationships/skus",
          "related": "https://yourdomain.commercelayer.io/api/shipping_categories/xYZkjABcde/skus"
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
