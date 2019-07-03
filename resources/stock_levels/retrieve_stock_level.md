---
description: How to fetch a specific stock level via API
---

# Retrieve a stock level

To fetch a single stock level, send a `GET` request to the `/api/stock_levels/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/stock_levels/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the stock level identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde \
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
    "type": "stock_levels",
    "links": {
      "self": "https://yourdomein.commercelayer.io/api/stock_levels/xYZkjABcde"
    },
    "attributes": {
      "priority": "1"
      "on_hold": "false"
      "created_at": "2018-01-01T12:00:00.000Z"
      "updated_at": "2018-01-01T12:00:00.000Z"
      "reference": "ANYREFEFERNCE"
      "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
      "stock_location": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde/relationships/stock_location",
            "related": "https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde/stock_location"
        }
      }
      "inventory_model": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde/relationships/inventory_model",
            "related": "https://yourdomain.commercelayer.io/api/stock_levels/xYZkjABcde/inventory_model"
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
