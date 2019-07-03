---
description: How to create a stock item via API
---

# Create a stock item

To create a new stock item, send a `POST` request to the `/api/stock_items` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain.commercelayer.io**/api/stock\_items**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**sku\_code** | `string` | Optional |
| attributes.**quantity** | `integer` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**stock\_location** | `object` | Required |
| relationships.**sku** | `object` | Required, if not set through the sku\_code attribute |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new stock item:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/stock_items \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "stock_items",
    "attributes": {
      "quantity": "100"
    },
    "relationships": {
      "stock_location": {
        "data": {
          "type": "stock_locations",
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
    "type": "stock_items",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/stock_items/xYZkjABcde"
    },
    "attributes": {
      "sku_code": "TSHIRTMM000000FFFFFFXLXX",
      "quantity": "100",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "stock_location": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stock_items/xYZkjABcde/relationships/stock_location",
          "related": "https://yourdomain.commercelayer.io/api/stock_items/xYZkjABcde/stock_location"
        }
      },
      "sku": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stock_items/xYZkjABcde/relationships/sku",
          "related": "https://yourdomain.commercelayer.io/api/stock_items/xYZkjABcde/sku"
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

