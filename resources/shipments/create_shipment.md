---
description: How to create a shipment via API
---

# Create a shipment

To create a new shipment, send a `POST` request to the `/api/shipments` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain.commercelayer.io**/api/shipments**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new shipment:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/shipments \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "shipments",
    "attributes": {
    },
    "relationships": {
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `shipment` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "shipments",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde"
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
}
```
{% endtab %}
{% endtabs %}

