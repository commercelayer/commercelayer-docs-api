---
description: How to fetch a specific SKU list via API
---

# Retrieve a SKU list

To fetch a single SKU list, send a `GET` request to the `/api/sku_lists/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/sku_lists/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the SKU list identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/sku_lists/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

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

