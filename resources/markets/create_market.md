---
description: How to create A market via API
---

# Create A market

To create a new market, send a `POST` request to the `/api/markets` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

```text
**POST** https://yourdomain.commercelayer.io**/api/markets**
```

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**number** | `integer` |  |
| attributes.**name** | `string` | required |
| attributes.**facebook_pixel_id** | `string` | optional |
| attributes.**id** | `string` | required |
| attributes.**created_at** | `datetime` | required |
| attributes.**updated_at** | `datetime` | required |
| attributes.**reference** | `string` | optional |
| attributes.**metadata** | `object` | optional |
| relationships.**merchant** | `has_one` | required |
| relationships.**price_list** | `has_one` | required |
| relationships.**inventory_model** | `has_one` | required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new market:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/markets \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "markets",
    "attributes": {
      "name": "EU Market"
    },
    "relationships": {
      "merchant": {
        "data": {
          "type": "merchants",
          "id": "zxcVBnMASd"
        }
      }
      "price_list": {
        "data": {
          "type": "price_lists",
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
On success, the API responds with a `201 Created` status code, returning the created `market` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "markets",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde"
    },
    "attributes": {
        "number": "1234"
        "name": "EU Market"
        "facebook_pixel_id": "1234567890"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
        "merchant": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/relationships/merchant",
              "related": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/merchant"
          }
        }
        "price_list": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/relationships/price_list",
              "related": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/price_list"
          }
        }
        "inventory_model": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/relationships/inventory_model",
              "related": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/inventory_model"
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
