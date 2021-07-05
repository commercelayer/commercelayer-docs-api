---
description: How to update an existing inventory return location via API
---

# Update an inventory return location

To update an existing inventory return location, send a `PATCH` request to the `/api/inventory_return_locations/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/inventory_return_locations/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**priority** | `integer` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**stock_location** | `object` | Optional |
| relationships.**inventory_model** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the inventory return location identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/inventory_return_locations/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "inventory_return_locations",
    "id": "xYZkjABcde",
    "attributes": {
      "reference": "ANY-EXTERNAL-REFEFERNCE"
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
    "type": "inventory_return_locations",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/inventory_return_locations/xYZkjABcde"
    },
    "attributes": {
      "priority": 1,
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
          "self": "https://yourdomain.commercelayer.io/api/inventory_return_locations/xYZkjABcde/relationships/stock_location",
          "related": "https://yourdomain.commercelayer.io/api/inventory_return_locations/xYZkjABcde/stock_location"
        }
      },
      "inventory_model": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/inventory_return_locations/xYZkjABcde/relationships/inventory_model",
          "related": "https://yourdomain.commercelayer.io/api/inventory_return_locations/xYZkjABcde/inventory_model"
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

