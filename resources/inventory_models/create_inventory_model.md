---
description: How to create An inventory model via API
---

# Create An inventory model

To create a new inventory model, send a `POST` request to the `/api/inventory_models` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https\://yourdomain.commercelayer.io**/api/inventory_models**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | required |
| attributes.**id** | `string` | required |
| attributes.**created_at** | `datetime` | required |
| attributes.**updated_at** | `datetime` | required |
| attributes.**reference** | `string` | optional |
| attributes.**metadata** | `object` | optional |
| relationships.**stock_levels** | `has_many` |  |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new inventory model:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/inventory_models \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "inventory_models",
    "attributes": {
      "name": "EU Inventory Model"
    },
    "relationships": {
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `inventory model` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "inventory_models",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/inventory_models/xYZkjABcde"
    },
    "attributes": {
        "name": "EU Inventory Model"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
        "stock_levels": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/inventory_models/xYZkjABcde/relationships/stock_levels",
              "related": "https://yourdomain.commercelayer.io/api/inventory_models/xYZkjABcde/stock_levels"
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
