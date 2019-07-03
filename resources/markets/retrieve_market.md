---
description: How to fetch a specific market via API
---

# Retrieve a market

To fetch a single market, send a `GET` request to the `/api/markets/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/markets/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the market identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/markets/xYZkjABcde \
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
    "type": "markets",
    "links": {
      "self": "https://yourdomein.commercelayer.io/api/markets/xYZkjABcde"
    },
    "attributes": {
      "number": "1234"
      "name": "EU Market"
      "facebook_pixel_id": "1234567890"
      "created_at": "2018-01-01T12:00:00.000Z"
      "updated_at": "2018-01-01T12:00:00.000Z"
      "reference": "ANYREFEFERNCE"
      "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
      "merchant": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/relationships/merchant",
            "related": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/merchant"
        }
      }
      "price_list": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/relationships/price_list",
            "related": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/price_list"
        }
      }
      "inventory_model": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/relationships/inventory_model",
            "related": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/inventory_model"
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
