---
description: How to fetch a specific inventory stock location via API
---

# Retrieve an inventory stock location

To fetch a single inventory stock location, send a `GET` request to the `/api/inventory_stock_locations/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/inventory\_stock\_locations/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the inventory stock location identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/inventory_stock_locations/xYZkjABcde \
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
    "type": "inventory_stock_locations",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/inventory_stock_locations/xYZkjABcde"
    },
    "attributes": {
      "priority": "1",
      "on_hold": "false",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "stock_location": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/inventory_stock_locations/xYZkjABcde/relationships/stock_location",
          "related": "https://yourdomain.commercelayer.io/api/inventory_stock_locations/xYZkjABcde/stock_location"
        }
      },
      "inventory_model": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/inventory_stock_locations/xYZkjABcde/relationships/inventory_model",
          "related": "https://yourdomain.commercelayer.io/api/inventory_stock_locations/xYZkjABcde/inventory_model"
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

