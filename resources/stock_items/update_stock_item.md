---
description: How to update an existing stock item via API
---

# Update a stock item

To update an existing stock item, send a `PATCH` request to the `/api/stock_items/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/stock_items/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**sku_code** | `string` | Optional |
| attributes.**quantity** | `integer` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**stock_location** | `object` | Required |
| relationships.**sku** | `object` | Required, if not set through the sku_code attribute |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the stock item identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/stock_items/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "stock_items",
    "id": "xYZkjABcde",
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
      "sku": {
        "data": {
          "type": "skus",
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
    "type": "stock_items",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/stock_items/xYZkjABcde"
    },
    "attributes": {
      "sku_code": "TSHIRTMM000000FFFFFFXLXX",
      "quantity": "100",
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
