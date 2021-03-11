---
description: How to fetch a collection of shipments via API
---

# List all shipments

To fetch a collection of shipments, send a `GET` request to the `/api/shipments` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/shipments**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of shipments:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/shipments/ \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a paginated collection of resource objects:

```javascript
{
  "data": [
    {
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
    },
    {
      "other": "... 9 shipments (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/shipments?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/shipments?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/shipments?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of shipments can be sorted by the following attributes:

* `status`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

