---
description: How to fetch a specific stock location via API
---

# Retrieve a stock location

To fetch a single stock location, send a `GET` request to the `/api/stock_locations/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/stock_locations/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the stock location identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde \
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
    "type": "stock_locations",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde"
    },
    "attributes": {
      "number": 1234,
      "name": "Primary warehouse",
      "label_format": "PDF",
      "suppress_etd": "false",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "address": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/address",
          "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/address"
        }
      },
      "stock_levels": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/stock_levels",
          "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/stock_levels"
        }
      },
      "stock_items": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/stock_items",
          "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/stock_items"
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
