---
description: How to create a return line item via API
---

# Create a return line item

To create a new return line item, send a `POST` request to the `/api/return_line_items` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/return_line_items**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**quantity** | `integer` | Required |
| attributes.**return_reason** | `object` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**return** | `object` | Required |
| relationships.**line_item** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new return line item:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/return_line_items \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "return_line_items",
    "attributes": {
      "quantity": null
    },
    "relationships": {
      "return": {
        "data": {
          "type": "returns",
          "id": "QWERtyUpBa"
        }
      },
      "line_item": {
        "data": {
          "type": "line_items",
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
    "type": "return_line_items",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/return_line_items/xYZkjABcde"
    },
    "attributes": {
      "sku_code": "TSHIRTMM000000FFFFFFXLXX",
      "name": "Black Men T-shirt with White Logo (XL)",
      "quantity": null,
      "return_reason": {
        "size": "was wrong"
      },
      "restocked_at": "2018-01-01T12:00:00.000Z",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "return": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/return_line_items/xYZkjABcde/relationships/return",
          "related": "https://yourdomain.commercelayer.io/api/return_line_items/xYZkjABcde/return"
        }
      },
      "line_item": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/return_line_items/xYZkjABcde/relationships/line_item",
          "related": "https://yourdomain.commercelayer.io/api/return_line_items/xYZkjABcde/line_item"
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

