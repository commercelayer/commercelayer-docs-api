---
description: How to create a price via API
---

# Create a price

To create a new price, send a `POST` request to the `/api/prices` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain.commercelayer.io**/api/prices**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**sku\_code** | `string` | Optional |
| attributes.**amount\_cents** | `integer` | Required |
| attributes.**compare\_at\_amount\_cents** | `integer` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**price\_list** | `object` | Required |
| relationships.**sku** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new price:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/prices \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "prices",
    "attributes": {
      "amount_cents": "10000"
      "compare_at_amount_cents": "13000"
    },
    "relationships": {
      "price_list": {
        "data": {
          "type": "price_lists",
          "id": "QWERtyUpBa"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `price` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "prices",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde"
    },
    "attributes": {
        "currency_code": "EUR"
        "sku_code": "TSHIRTMM000000FFFFFFXLXX"
        "amount_cents": "10000"
        "amount_float": "100.0"
        "formatted_amount": "€100,00"
        "compare_at_amount_cents": "13000"
        "compare_at_amount_float": "130.00"
        "formatted_compare_at_amount": "€130,00"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
        "price_list": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde/relationships/price_list",
              "related": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde/price_list"
          }
        }
        "sku": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde/relationships/sku",
              "related": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde/sku"
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

