---
description: How to create a market via API
---

# Create a market

To create a new market, send a `POST` request to the `/api/markets` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/markets**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**facebook_pixel_id** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**merchant** | `object` | Required |
| relationships.**price_list** | `object` | Required |
| relationships.**inventory_model** | `object` | Required |

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
          "id": "QWERtyUpBa"
        }
      }
      "price_list": {
        "data": {
          "type": "price_lists",
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
On success, the API responds with a `201 Created` status code, returning the created `market` object:

```javascript
{
  "data": {
    "id": "{{market_id}}",
    "type": "markets",
    "links": {
      "self": "https://{{subdomain}}.commercelayer.io/api/markets/{{market_id}}"
    },
    "attributes": {
      "number": 1234,
      "name": "EU Market",
      "facebook_pixel_id": "1234567890",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "merchant": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/markets/{{market_id}}/relationships/merchant",
          "related": "https://{{subdomain}}.commercelayer.io/api/markets/{{market_id}}/merchant"
        }
      },
      "price_list": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/markets/{{market_id}}/relationships/price_list",
          "related": "https://{{subdomain}}.commercelayer.io/api/markets/{{market_id}}/price_list"
        }
      },
      "inventory_model": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/markets/{{market_id}}/relationships/inventory_model",
          "related": "https://{{subdomain}}.commercelayer.io/api/markets/{{market_id}}/inventory_model"
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
