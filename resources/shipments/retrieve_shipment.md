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
      "cost_amount_cents": 1000,
      "cost_amount_float": 10.0,
      "formatted_cost_amount": "€10,00",
      "skus_count": 2,
      "selected_rate_id": "rate_f89e4663c3ed47ee94d37763f6d21d54",
      "rates": [
        {
          "id": "rate_f89e4663c3ed47ee94d37763f6d21d54",
          "rate": "45.59",
          "carrier": "DHLExpress",
          "service": "MedicalExpress"
        }
      ],
      "purchase_error_code": "SHIPMENT.POSTAGE.FAILURE",
      "purchase_error_message": "Account not allowed for this service.",
      "get_rates_started_at": "2018-01-01T12:00:00.000Z",
      "get_rates_completed_at": "2018-01-01T12:00:00.000Z",
      "purchase_started_at": "2018-01-01T12:00:00.000Z",
      "purchase_completed_at": "2018-01-01T12:00:00.000Z",
      "purchase_failed_at": "2018-01-01T12:00:00.000Z",
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
      "origin_address": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/origin_address",
          "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/origin_address"
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
      "delivery_lead_time": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/delivery_lead_time",
          "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/delivery_lead_time"
        }
      },
      "shipment_line_items": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/shipment_line_items",
          "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/shipment_line_items"
        }
      },
      "stock_line_items": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/stock_line_items",
          "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/stock_line_items"
        }
      },
      "stock_transfers": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/stock_transfers",
          "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/stock_transfers"
        }
      },
      "available_shipping_methods": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/available_shipping_methods",
          "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/available_shipping_methods"
        }
      },
      "carrier_accounts": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/carrier_accounts",
          "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/carrier_accounts"
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

