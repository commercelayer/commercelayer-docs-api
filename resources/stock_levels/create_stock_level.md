---
description: How to create A stock level via API
---

# Create A stock level

To create a new stock level, send a `POST` request to the `/api/stock_levels` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/stock_levels**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**priority** | `integer` | required |
| attributes.**on_hold** | `boolean` | optional |
| attributes.**id** | `string` | required |
| attributes.**created_at** | `datetime` | required |
| attributes.**updated_at** | `datetime` | required |
| attributes.**reference** | `string` | optional |
| attributes.**metadata** | `object` | optional |
| relationships.**stock_location** | `has_one` | required |
| relationships.**inventory_model** | `has_one` | required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new stock level:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/stock_levels \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "stock_levels",
    "attributes": {
      "priority": "1"
    },
    "relationships": {
      "stock_location": {
        "data": {
          "type": "stock_locations",
          "id": "zxcVBnMASd"
        }
      }
      "inventory_model": {
        "data": {
          "type": "inventory_models",
          "id": "zxcVBnMASd"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `stock level` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "stock_levels",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde"
    },
    "attributes": {
        "priority": "1"
        "on_hold": "false"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
        "stock_location": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde/relationships/stock_location",
              "related": "https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde/stock_location"
          }
        }
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
