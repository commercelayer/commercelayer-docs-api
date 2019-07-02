---
description: How to create A shipment via API
---

# Create A shipment

To create a new shipment, send a `POST` request to the `/api/shipments` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/shipments**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**number** | `string` |  |
| attributes.**status** | `string` |  |
| attributes.**currency_code** | `string` |  |
| attributes.**cost_amount_cents** | `integer` |  |
| attributes.**cost_amount_float** | `float` |  |
| attributes.**formatted_cost_amount** | `string` |  |
| attributes.**_on_hold** | `integer, value is '1'` | optional |
| attributes.**_picking** | `integer, value is '1'` | optional |
| attributes.**_packing** | `integer, value is '1'` | optional |
| attributes.**_ready_to_ship** | `integer, value is '1'` | optional |
| attributes.**_ship** | `integer, value is '1'` | optional |
| attributes.**_get_rates** | `integer, value is '1'` | optional |
| attributes.**selected_rate_id** | `string` | optional |
| attributes.**_purchase** | `integer, value is '1'` | optional |
| attributes.**id** | `string` | required |
| attributes.**created_at** | `datetime` | required |
| attributes.**updated_at** | `datetime` | required |
| attributes.**reference** | `string` | optional |
| attributes.**metadata** | `object` | optional |
| relationships.**shipping_category** | `has_one` |  |
| relationships.**stock_location** | `has_one` |  |
| relationships.**shipping_address** | `has_one` |  |
| relationships.**shipping_method** | `has_one` | optional |
| relationships.**shipment_line_items** | `has_many` |  |
| relationships.**available_shipping_methods** | `has_many` |  |
| relationships.**parcels** | `has_many` |  |
| relationships.**attachments** | `has_many` |  |

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
        "number": "#1234/S/001"
        "status": "draft"
        "currency_code": "EUR"
        "cost_amount_cents": "1000"
        "cost_amount_float": "10.00"
        "formatted_cost_amount": "€10,00"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
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
