---
description: How to update an existing shipment via API
---

# Update a shipment

To update an existing shipment, send a `PATCH` request to the `/api/shipments/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://yourdomain.commercelayer.io**/api/shipments/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**\_on\_hold** | `boolean, value is 'true'` | Optional |
| attributes.**\_picking** | `boolean, value is 'true'` | Optional |
| attributes.**\_packing** | `boolean, value is 'true'` | Optional |
| attributes.**\_ready\_to\_ship** | `boolean, value is 'true'` | Optional |
| attributes.**\_ship** | `boolean, value is 'true'` | Optional |
| attributes.**\_get\_rates** | `boolean, value is 'true'` | Optional |
| attributes.**selected\_rate\_id** | `string` | Optional |
| attributes.**\_purchase** | `boolean, value is 'true'` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**shipping\_method** | `object` | Optional |

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
    "id": "xYZkjABcde"
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

