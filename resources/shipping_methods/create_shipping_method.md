---
description: How to create a shipping method via API
---

# Create a shipping method

To create a new shipping method, send a `POST` request to the `/api/shipping_methods` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/shipping_methods**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**price_amount_cents** | `integer` | Required |
| attributes.**free_over_amount_cents** | `integer` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**market** | `object` | Required |
| relationships.**shipping_zone** | `object` | Required |
| relationships.**shipping_category** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new shipping method:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/shipping_methods \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "shipping_methods",
    "attributes": {
      "name": "Standard shipping",
      "price_amount_cents": "1000"
    },
    "relationships": {
      "market": {
        "data": {
          "type": "markets",
          "id": "QWERtyUpBa"
        }
      }
      "shipping_zone": {
        "data": {
          "type": "shipping_zones",
          "id": "QWERtyUpBa"
        }
      }
      "shipping_category": {
        "data": {
          "type": "shipping_categories",
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
    "type": "shipping_methods",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde"
    },
    "attributes": {
      "name": "Standard shipping",
      "disabled_at": "2018-01-01T12:00:00.000Z",
      "currency_code": "EUR",
      "price_amount_cents": "1000",
      "price_amount_float": "10.00",
      "formatted_price_amount": "€10,00",
      "free_over_amount_cents": "9900",
      "free_over_amount_float": "99.00",
      "formatted_free_over_amount": "€99,00",
      "price_amount_for_shipment_cents": "0",
      "price_amount_for_shipment_float": "0.0",
      "formatted_price_amount_for_shipment": "€0,00",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "market": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/relationships/market",
          "related": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/market"
        }
      },
      "shipping_zone": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/relationships/shipping_zone",
          "related": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/shipping_zone"
        }
      },
      "shipping_category": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/relationships/shipping_category",
          "related": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/shipping_category"
        }
      },
      "delivery_lead_time_for_shipment": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/relationships/delivery_lead_time_for_shipment",
          "related": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/delivery_lead_time_for_shipment"
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
