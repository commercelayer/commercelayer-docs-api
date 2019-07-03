---
description: How to fetch a specific shipment via API
---

# Retrieve a shipment

To fetch a single shipment, send a `GET` request to the `/api/shipments/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/shipments/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the shipment identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde \
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
    "type": "shipments",
    "links": {
      "self": "https://yourdomein.commercelayer.io/api/shipments/xYZkjABcde"
    },
    "attributes": {
      "number": "#1234/S/001",
      "status": "draft",
      "currency_code": "EUR",
      "cost_amount_cents": "1000",
      "cost_amount_float": "10.00",
      "formatted_cost_amount": "€10,00",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
        "foo": "bar"
        },
    },
    "relationships": {
      "shipping_category": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/shipping_category",
            "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/shipping_category"
        }
      },
      "stock_location": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/stock_location",
            "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/stock_location"
        }
      },
      "shipping_address": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/shipping_address",
            "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/shipping_address"
        }
      },
      "shipping_method": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/shipping_method",
            "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/shipping_method"
        }
      },
      "shipment_line_items": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/shipment_line_items",
            "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/shipment_line_items"
        }
      },
      "available_shipping_methods": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/available_shipping_methods",
            "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/available_shipping_methods"
        }
      },
      "parcels": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/parcels",
            "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/parcels"
        }
      },
      "attachments": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/attachments",
            "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/attachments"
        }
      },
    },
    "meta": {
      "mode": "test"
    }
  }
}
```
{% endtab %}
{% endtabs %}
