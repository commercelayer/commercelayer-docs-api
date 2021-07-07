---
description: How to update an existing line item option via API
---

# Update a line item option

To update an existing line item option, send a `PATCH` request to the `/api/line_item_options/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://yourdomain.commercelayer.io**/api/line\_item\_options/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**name** | `string` | Optional |
| attributes.**quantity** | `integer` | Optional |
| attributes.**options** | `object` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**sku\_option** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the line item option identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/line_item_options/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "line_item_options",
    "id": "xYZkjABcde",
    "attributes": {
      "name": "Embossing"
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

