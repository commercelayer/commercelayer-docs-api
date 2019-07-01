---
description: How to create a SKU via API
---

# Create an SKU

To create a new SKU, send a `POST` request to the `/api/skus` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain.commercelayer.io**/api/skus**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**code** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**description** | `string` | Optional |
| attributes.**image\_url** | `string` | Optional |
| attributes.**tag\_names** | `string` | Optional |
| attributes.**pieces\_per\_pack** | `integer` | Optional |
| attributes.**weight** | `float` | Optional |
| attributes.**unit\_of\_weight** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**shipping\_category** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new SKU:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/skus \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -d '{
  "data": {
    "type": "skus",
    "attributes": {
      "code": "TSHIRTMM000000FFFFFFXLXX",
      "name": "Black Men T-shirt with White Logo (XL)"
    },
    "relationships": {
      "shipping_category": {
        "data": {
          "type": "shipping_categories",
          "id": "1234"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `sku` object:

```javascript
{
  "data": {
    "id": "1234",
    "type": "skus",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/skus/1234"
    },
        "attributes": {
            "code": "TSHIRTMM000000FFFFFFXLXX",
            "name": "Black Men T-shirt with White Logo (XL)",
            "description": null,
            "image_url": null,
            "tag_names": "",
            "pieces_per_pack": null,
            "weight": null,
            "unit_of_weight": null,
            "created_at": "2018-01-01T12:00:00.000Z",
            "updated_at": "2018-01-01T12:00:00.000Z",
            "reference": null,
            "metadata": {}
        },
        "relationships": {
            "shipping_category": {
                "links": {
                    "self": "https://yourdomain.commercelayer.io/api/skus/1234/relationships/shipping_category",
                    "related": "https://yourdomain.commercelayer.io/api/skus/1234/shipping_category"
                }
            },
            "prices": {
                "links": {
                    "self": "https://yourdomain.commercelayer.io/api/skus/1234/relationships/prices",
                    "related": "https://yourdomain.commercelayer.io/api/skus/1234/prices"
                }
            },
            "stock_items": {
                "links": {
                    "self": "https://yourdomain.commercelayer.io/api/skus/1234/relationships/stock_items",
                    "related": "https://yourdomain.commercelayer.io/api/skus/1234/stock_items"
                }
            },
            "delivery_lead_times": {
                "links": {
                    "self": "https://yourdomain.commercelayer.io/api/skus/1234/relationships/delivery_lead_times",
                    "related": "https://yourdomain.commercelayer.io/api/skus/1234/delivery_lead_times"
                }
            },
            "sku_options": {
                "links": {
                    "self": "https://yourdomain.commercelayer.io/api/skus/1234/relationships/sku_options",
                    "related": "https://yourdomain.commercelayer.io/api/skus/1234/sku_options"
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

