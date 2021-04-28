---
description: How to fetch a specific SKU list item via API
---

# Retrieve a SKU list item

To fetch a single SKU list item, send a `GET` request to the `/api/sku_list_items/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/sku\_list\_items/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the SKU list item identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/sku_list_items/xYZkjABcde \
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
    "type": "sku_list_items",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/sku_list_items/xYZkjABcde"
    },
    "attributes": {
      "position": 2,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "sku_list": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/sku_list_items/xYZkjABcde/relationships/sku_list",
          "related": "https://yourdomain.commercelayer.io/api/sku_list_items/xYZkjABcde/sku_list"
        }
      },
      "sku": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/sku_list_items/xYZkjABcde/relationships/sku",
          "related": "https://yourdomain.commercelayer.io/api/sku_list_items/xYZkjABcde/sku"
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

