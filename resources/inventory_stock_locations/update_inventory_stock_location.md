---
description: How to update an existing inventory stock location via API
---

# Update an inventory stock location

To update an existing inventory stock location, send a `PATCH` request to the `/api/inventory_stock_locations/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://yourdomain.commercelayer.io**/api/inventory\_stock\_locations/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**priority** | `integer` | Optional |
| attributes.**on\_hold** | `boolean` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**stock\_location** | `object` | Optional |
| relationships.**inventory\_model** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the inventory stock location identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/inventory_stock_locations/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "inventory_stock_locations",
    "id": "xYZkjABcde",
    "attributes": {
      "on_hold": "false"
    }
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
    "type": "inventory_stock_locations",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/inventory_stock_locations/xYZkjABcde"
    },
    "attributes": {
      "priority": 1,
      "on_hold": false,
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

