---
description: How to create a line item option via API
---

# Create a line item option

To create a new line item option, send a `POST` request to the `/api/line_item_options` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain.commercelayer.io**/api/line\_item\_options**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | Optional |
| attributes.**quantity** | `integer` | Required |
| attributes.**options** | `object` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**line\_item** | `object` | Required |
| relationships.**sku\_option** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new line item option:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/line_item_options \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "line_item_options",
    "attributes": {
      "quantity": "2",
      "options": {
        "embossing_text": "Happy Birthday!"
      }
    },
    "relationships": {
      "line_item": {
        "data": {
          "type": "line_items",
          "id": "QWERtyUpBa"
        }
      },
      "sku_option": {
        "data": {
          "type": "sku_options",
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
    "type": "line_item_options",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/line_item_options/xYZkjABcde"
    },
    "attributes": {
      "name": "Embossing",
      "quantity": 2,
      "currency_code": "EUR",
      "unit_amount_cents": 990,
      "unit_amount_float": 9.9,
      "formatted_unit_amount": "€9,90",
      "total_amount_cents": 1880,
      "total_amount_float": 18.8,
      "formatted_total_amount": "€18,80",
      "delay_hours": 48,
      "delay_days": 2,
      "options": {
        "embossing_text": "Happy Birthday!"
      },
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "line_item": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/line_item_options/xYZkjABcde/relationships/line_item",
          "related": "https://yourdomain.commercelayer.io/api/line_item_options/xYZkjABcde/line_item"
        }
      },
      "sku_option": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/line_item_options/xYZkjABcde/relationships/sku_option",
          "related": "https://yourdomain.commercelayer.io/api/line_item_options/xYZkjABcde/sku_option"
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

