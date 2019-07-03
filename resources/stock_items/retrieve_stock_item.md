---
description: How to fetch a specific stock item via API
---

# Retrieve a stock item

To fetch a single stock item, send a `GET` request to the `/api/stock_items/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/stock_items/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the stock item identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/stock_items/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

```javascript
{
  "data": {
    "id": "{{stock_item_id}}",
    "type": "stock_items",
    "links": {
      "self": "https://{{subdomain}}.commercelayer.io/api/stock_items/{{stock_item_id}}"
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
          "self": "https://{{subdomain}}.commercelayer.io/api/stock_items/{{stock_item_id}}/relationships/stock_location",
          "related": "https://{{subdomain}}.commercelayer.io/api/stock_items/{{stock_item_id}}/stock_location"
        }
      },
      "sku": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/stock_items/{{stock_item_id}}/relationships/sku",
          "related": "https://{{subdomain}}.commercelayer.io/api/stock_items/{{stock_item_id}}/sku"
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
