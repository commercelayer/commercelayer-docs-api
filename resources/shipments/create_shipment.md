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
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**order** | `object` | Required |

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
    "relationships": {
      "order": {
        "data": {
          "type": "orders",
          "id": "QWERtyUpBa"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created resource object:

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
      "skus_count": "2",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "order": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/order",
          "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/order"
        }
      },
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

