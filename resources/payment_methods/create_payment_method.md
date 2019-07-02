---
description: How to create A payment method via API
---

# Create A payment method

To create a new payment method, send a `POST` request to the `/api/payment_methods` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/payment_methods**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**payment_source_type** | `string` | required |
| attributes.**name** | `string` |  |
| attributes.**disabled_at** | `datetime` | optional |
| attributes.**price_amount_cents** | `integer` | required |
| attributes.**price_amount_float** | `float` |  |
| attributes.**formatted_price_amount** | `string` |  |
| attributes.**id** | `string` | required |
| attributes.**created_at** | `datetime` | required |
| attributes.**updated_at** | `datetime` | required |
| attributes.**reference** | `string` | optional |
| attributes.**metadata** | `object` | optional |
| relationships.**market** | `has_one` | required |
| relationships.**payment_gateway** | `has_one` | required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new payment method:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/payment_methods \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "payment_methods",
    "attributes": {
      "payment_source_type": "CreditCard"
      "price_amount_cents": "0"
    },
    "relationships": {
      "market": {
        "data": {
          "type": "markets",
          "id": "zxcVBnMASd"
        }
      }
      "payment_gateway": {
        "data": {
          "type": "payment_gateways",
          "id": "zxcVBnMASd"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `payment method` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "payment_methods",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/payment_methods/xYZkjABcde"
    },
    "attributes": {
        "payment_source_type": "CreditCard"
        "name": "Credit Card"
        "disabled_at": "2018-01-01T12:00:00.000Z"
        "price_amount_cents": "0"
        "price_amount_float": "0.0"
        "formatted_price_amount": "€0,00"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
        "market": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/payment_methods/xYZkjABcde/relationships/market",
              "related": "https://yourdomain.commercelayer.io/api/payment_methods/xYZkjABcde/market"
          }
        }
        "payment_gateway": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/payment_methods/xYZkjABcde/relationships/payment_gateway",
              "related": "https://yourdomain.commercelayer.io/api/payment_methods/xYZkjABcde/payment_gateway"
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
