---
description: How to fetch a specific shipment via API
---

# Retrieve a shipment

To fetch a single shipment, send a `GET` request to the `/api/shipments/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/shipments/:id**

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
  "id": "{{shipment_id}}",
  "type": "shipments",
  "links": {
    "self": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}"
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
    }
  },
  "relationships": {
    "shipping_category": {
      "links": {
        "self": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/relationships/shipping_category",
        "related": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/shipping_category"
      }
    },
    "stock_location": {
      "links": {
        "self": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/relationships/stock_location",
        "related": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/stock_location"
      }
    },
    "shipping_address": {
      "links": {
        "self": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/relationships/shipping_address",
        "related": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/shipping_address"
      }
    },
    "shipping_method": {
      "links": {
        "self": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/relationships/shipping_method",
        "related": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/shipping_method"
      }
    },
    "shipment_line_items": {
      "links": {
        "self": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/relationships/shipment_line_items",
        "related": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/shipment_line_items"
      }
    },
    "available_shipping_methods": {
      "links": {
        "self": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/relationships/available_shipping_methods",
        "related": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/available_shipping_methods"
      }
    },
    "parcels": {
      "links": {
        "self": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/relationships/parcels",
        "related": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/parcels"
      }
    },
    "attachments": {
      "links": {
        "self": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/relationships/attachments",
        "related": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/attachments"
      }
    }
  },
  "meta": {
    "mode": "test"
  }
}
```
{% endtab %}
{% endtabs %}

