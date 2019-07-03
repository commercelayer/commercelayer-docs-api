---
description: How to fetch a specific delivery lead time via API
---

# Retrieve a delivery lead time

To fetch a single delivery lead time, send a `GET` request to the `/api/delivery_lead_times/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/delivery_lead_times/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the delivery lead time identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/delivery_lead_times/xYZkjABcde \
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
    "type": "delivery_lead_times",
    "links": {
      "self": "https://yourdomein.commercelayer.io/api/delivery_lead_times/xYZkjABcde"
    },
    "attributes": {
      "min_hours": "48"
      "max_hours": "72"
      "min_days": "2"
      "max_days": "3"
      "created_at": "2018-01-01T12:00:00.000Z"
      "updated_at": "2018-01-01T12:00:00.000Z"
      "reference": "ANYREFEFERNCE"
      "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
      "stock_location": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/delivery_lead_times/xYZkjABcde/relationships/stock_location",
            "related": "https://yourdomain.commercelayer.io/api/delivery_lead_times/xYZkjABcde/stock_location"
        }
      }
      "shipping_method": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/delivery_lead_times/xYZkjABcde/relationships/shipping_method",
            "related": "https://yourdomain.commercelayer.io/api/delivery_lead_times/xYZkjABcde/shipping_method"
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
