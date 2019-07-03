---
description: How to update an existing shipping method via API
---

# Update a shipping method

To update an existing shipping method, send a `PATCH` request to the `/api/shipping_methods/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/shipping_methods/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
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
The following request updates the shipping method identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "shipping_methods",
    "id": "xYZkjABcde",
    "attributes": {
      "name": "Standard shipping"
      "price_amount_cents": "1000"
      "free_over_amount_cents": "9900"
      "reference": "ANYREFEFERNCE"
      "metadata": "{:foo=>"bar"}"
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
On success, the API responds with a `200 OK` status code, returning the updated resource object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "shipping_methods",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde"
    },
    "attributes": {
        "name": "Standard shipping"
        "disabled_at": "2018-01-01T12:00:00.000Z"
        "currency_code": "EUR"
        "price_amount_cents": "1000"
        "price_amount_float": "10.00"
        "formatted_price_amount": "€10,00"
        "free_over_amount_cents": "9900"
        "free_over_amount_float": "99.00"
        "formatted_free_over_amount": "€99,00"
        "price_amount_for_shipment_cents": "0"
        "price_amount_for_shipment_float": "0.0"
        "formatted_price_amount_for_shipment": "€0,00"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{
  "foo": "bar"
}"
    },
    "relationships": {
        "market": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/relationships/market",
              "related": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/market"
          }
        }
        "shipping_zone": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/relationships/shipping_zone",
              "related": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/shipping_zone"
          }
        }
        "shipping_category": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/relationships/shipping_category",
              "related": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/shipping_category"
          }
        }
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
