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
| attributes.**suppress_etd** | `boolean` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
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
On success, the API responds with a `201 Created` status code, returning the created resource object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "stock_locations",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde"
    },
    "attributes": {
      "number": 1234,
      "name": "Primary warehouse",
      "label_format": "PDF",
      "suppress_etd": false,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "address": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/address",
          "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/address"
        }
      },
      "inventory_stock_locations": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/inventory_stock_locations",
          "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/inventory_stock_locations"
        }
      },
      "inventory_return_locations": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/inventory_return_locations",
          "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/inventory_return_locations"
        }
      },
      "stock_items": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/stock_items",
          "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/stock_items"
        }
      },
      "stock_transfers": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/stock_transfers",
          "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/stock_transfers"
        }
      },
      "attachments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/attachments",
          "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/attachments"
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

