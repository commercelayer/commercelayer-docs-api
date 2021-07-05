---
description: How to create a SKU list via API
---

# Create a SKU list

To create a new SKU list, send a `POST` request to the `/api/sku_lists` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/sku_lists**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**description** | `string` | Optional |
| attributes.**manual** | `boolean` | Optional, default is 'true' |
| attributes.**sku_code_regex** | `string` | Required, if manual is falsy |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new SKU list:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/sku_lists \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "sku_lists",
    "attributes": {
      "name": "Personal list",
      "sku_code_regex": "^(A|B).*$"
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
    "type": "sku_lists",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/sku_lists/xYZkjABcde"
    },
    "attributes": {
      "name": "Personal list",
      "slug": "personal-list-1",
      "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
      "manual": false,
      "sku_code_regex": "^(A|B).*$",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "skus": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/sku_lists/xYZkjABcde/relationships/skus",
          "related": "https://yourdomain.commercelayer.io/api/sku_lists/xYZkjABcde/skus"
        }
      },
      "sku_list_items": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/sku_lists/xYZkjABcde/relationships/sku_list_items",
          "related": "https://yourdomain.commercelayer.io/api/sku_lists/xYZkjABcde/sku_list_items"
        }
      },
      "bundles": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/sku_lists/xYZkjABcde/relationships/bundles",
          "related": "https://yourdomain.commercelayer.io/api/sku_lists/xYZkjABcde/bundles"
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

