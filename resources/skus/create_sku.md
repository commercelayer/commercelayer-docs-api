---
description: How to create an SKU via API
---

# Create an SKU

To create a new SKU, send a `POST` request to the `/api/skus` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/skus**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**code** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**description** | `string` | Optional |
| attributes.**image_url** | `string` | Optional |
| attributes.**tag_names** | `string` | Optional |
| attributes.**pieces_per_pack** | `integer` | Optional |
| attributes.**weight** | `float` | Optional |
| attributes.**unit_of_weight** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**shipping_category** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new SKU:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/skus \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "skus",
    "attributes": {
      "code": "TSHIRTMM000000FFFFFFXLXX"
      "name": "Black Men T-shirt with White Logo (XL)"
    },
    "relationships": {
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
On success, the API responds with a `201 Created` status code, returning the created `SKU` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "skus",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde"
    },
    "attributes": {
        "code": "TSHIRTMM000000FFFFFFXLXX"
        "name": "Black Men T-shirt with White Logo (XL)"
        "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
        "image_url": "https://img.yourbrand.com/skus/xYZkjABcde.png"
        "tag_names": "Men, Black, XL"
        "pieces_per_pack": "6"
        "weight": "300"
        "unit_of_weight": "gr"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{
  "foo": "bar"
}"
    },
    "relationships": {
        "shipping_category": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/shipping_category",
              "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/shipping_category"
          }
        }
        "prices": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/prices",
              "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/prices"
          }
        }
        "stock_items": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/stock_items",
              "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/stock_items"
          }
        }
        "delivery_lead_times": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/delivery_lead_times",
              "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/delivery_lead_times"
          }
        }
        "sku_options": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/sku_options",
              "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/sku_options"
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
