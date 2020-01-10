---
description: How to fetch a specific line item option via API
---

# Retrieve a line item option

To fetch a single line item option, send a `GET` request to the `/api/line_item_options/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/line_item_options/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the line item option identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/line_item_options/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

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
      "quantity": "2",
      "currency_code": "EUR",
      "unit_amount_cents": "990",
      "unit_amount_float": "9.9",
      "formatted_unit_amount": "€9,90",
      "total_amount_cents": "1880",
      "total_amount_float": "18.8",
      "formatted_total_amount": "€18,80",
      "delay_hours": "48",
      "delay_days": "2",
      "options": {
        "embossing_text": "Happy Birthday!"
      },
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
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
