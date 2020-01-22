---
description: How to update an existing stock level via API
---

# Update a stock level

To update an existing stock level, send a `PATCH` request to the `/api/stock_levels/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/stock_levels/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**priority** | `integer` | Required |
| attributes.**on_hold** | `boolean` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**stock_location** | `object` | Required |
| relationships.**inventory_model** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the stock level identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "stock_levels",
    "id": "xYZkjABcde",
    "attributes": {
      "priority": "1"
    },
    "relationships": {
      "stock_location": {
        "data": {
          "type": "stock_locations",
          "id": "QWERtyUpBa"
        }
      }
      "inventory_model": {
        "data": {
          "type": "inventory_models",
          "id": "QWERtyUpBa"
        }
      }
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
    "type": "stock_levels",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde"
    },
    "attributes": {
      "priority": "1",
      "on_hold": "false",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "stock_location": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde/relationships/stock_location",
          "related": "https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde/stock_location"
        }
      },
      "inventory_model": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde/relationships/inventory_model",
          "related": "https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde/inventory_model"
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
