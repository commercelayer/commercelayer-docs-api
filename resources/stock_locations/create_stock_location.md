---
description: How to create a stock location via API
---

# Create a stock location

To create a new stock location, send a `POST` request to the `/api/stock_locations` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/stock_locations**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**label_format** | `string` | Optional, default is 'pdf' |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**address** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new stock location:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/stock_locations \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "stock_locations",
    "attributes": {
      "name": "Primary warehouse"
    },
    "relationships": {
      "address": {
        "data": {
          "type": "addresses",
          "id": "QWERtyUpBa"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `stock location` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "stock_locations",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde"
    },
    "attributes": {
        "name": "Primary warehouse"
        "label_format": "PDF"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
        "address": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/address",
              "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/address"
          }
        }
        "stock_levels": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/stock_levels",
              "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/stock_levels"
          }
        }
        "stock_items": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/stock_items",
              "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/stock_items"
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
