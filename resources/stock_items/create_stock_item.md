---
description: How to create A stock item via API
---

# Create A stock item

To create a new stock item, send a `POST` request to the `/api/stock_items` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain&#46;commercelayer&#46;io**/api/stock_items**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**sku_code** | `string` | optional |
| attributes.**quantity** | `integer` | required |
| attributes.**id** | `string` | required |
| attributes.**created_at** | `datetime` | required |
| attributes.**updated_at** | `datetime` | required |
| attributes.**reference** | `string` | optional |
| attributes.**metadata** | `object` | optional |
| relationships.**stock_location** | `has_one` | required |
| relationships.**sku** | `has_one` | required, if not set through the sku_code attribute |

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
          "id": "zxcVBnMASd"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `stock item` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "stock_items",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/stock_items/xYZkjABcde"
    },
    "attributes": {
        "sku_code": "TSHIRTMM000000FFFFFFXLXX"
        "quantity": "100"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
        "stock_location": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/stock_items/xYZkjABcde/relationships/stock_location",
              "related": "https://yourdomain.commercelayer.io/api/stock_items/xYZkjABcde/stock_location"
          }
        }
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
