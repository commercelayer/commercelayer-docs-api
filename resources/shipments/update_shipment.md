---
description: How to update an existing shipment via API
---

# Update a shipment

To update an existing shipment, send a `PATCH` request to the `/api/shipments/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/shipments/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**_on_hold** | `integer, value is '1'` | Optional |
| attributes.**_picking** | `integer, value is '1'` | Optional |
| attributes.**_packing** | `integer, value is '1'` | Optional |
| attributes.**_ready_to_ship** | `integer, value is '1'` | Optional |
| attributes.**_ship** | `integer, value is '1'` | Optional |
| attributes.**_get_rates** | `integer, value is '1'` | Optional |
| attributes.**selected_rate_id** | `string` | Optional |
| attributes.**_purchase** | `integer, value is '1'` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**shipping_method** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the shipment identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "shipments",
    "id": "xYZkjABcde",
    "attributes": {
      "_on_hold": ""
      "_picking": ""
      "_packing": ""
      "_ready_to_ship": ""
      "_ship": ""
      "_get_rates": ""
      "selected_rate_id": "rate_f89e4663c3ed47ee94d37763f6d21d54"
      "_purchase": ""
      "reference": "ANYREFEFERNCE"
      "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
      "shipping_method": {
        "data": {
          "type": "shipping_methods",
          "id": "QWERtyUpBa"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning the updated resource object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "shipments",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde"
    },
    "attributes": {
        "number": "#1234/S/001"
        "status": "draft"
        "currency_code": "EUR"
        "cost_amount_cents": "1000"
        "cost_amount_float": "10.00"
        "formatted_cost_amount": "€10,00"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": {
  "foo": "bar"
}
    },
    "relationships": {
        "shipping_category": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/shipping_category",
              "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/shipping_category"
          }
        }
        "stock_location": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/stock_location",
              "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/stock_location"
          }
        }
        "shipping_address": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/shipping_address",
              "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/shipping_address"
          }
        }
        "shipping_method": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/shipping_method",
              "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/shipping_method"
          }
        }
        "shipment_line_items": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/shipment_line_items",
              "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/shipment_line_items"
          }
        }
        "available_shipping_methods": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/available_shipping_methods",
              "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/available_shipping_methods"
          }
        }
        "parcels": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/relationships/parcels",
              "related": "https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde/parcels"
          }
        }
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
