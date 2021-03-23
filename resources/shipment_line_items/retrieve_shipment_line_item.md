---
description: How to fetch a specific shipment line item via API
---

# Retrieve a shipment line item

To fetch a single shipment line item, send a `GET` request to the `/api/shipment_line_items/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/shipment_line_items/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the shipment line item identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/shipment_line_items/xYZkjABcde \
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
    "type": "shipment_line_items",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/shipment_line_items/xYZkjABcde"
    },
    "attributes": {
      "sku_code": "TSHIRTMM000000FFFFFFXLXX",
      "quantity": 0,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "shipment": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipment_line_items/xYZkjABcde/relationships/shipment",
          "related": "https://yourdomain.commercelayer.io/api/shipment_line_items/xYZkjABcde/shipment"
        }
      },
      "line_item": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipment_line_items/xYZkjABcde/relationships/line_item",
          "related": "https://yourdomain.commercelayer.io/api/shipment_line_items/xYZkjABcde/line_item"
        }
      },
      "stock_item": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipment_line_items/xYZkjABcde/relationships/stock_item",
          "related": "https://yourdomain.commercelayer.io/api/shipment_line_items/xYZkjABcde/stock_item"
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

