---
description: How to create a sku via API
---

# Create a sku

To create a new sku, send a `POST` request to the `/api/skus` endpoint, passing the resource arguments in the request body.

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
The following request creates a new sku:

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
On success, the API responds with a `201 Created` status code, returning the created resource object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "skus",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde"
    },
    "attributes": {
      "code": "TSHIRTMM000000FFFFFFXLXX",
      "name": "Black Men T-shirt with White Logo (XL)",
      "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
      "image_url": "https://img.yourdomain.com/skus/xYZkjABcde.png",
      "tag_names": "Men, Black, XL",
      "pieces_per_pack": "6",
      "weight": "300",
      "unit_of_weight": "gr",
      "inventory": {
        "available": true,
        "quantity": 10,
        "levels": [
          {
            "quantity": 4,
            "delivery_lead_times": [
              {
                "shipping_method": {
                  "name": "Standard Shipping",
                  "reference": null,
                  "price_amount_cents": 700,
                  "free_over_amount_cents": 9900,
                  "formatted_price_amount": "€7,00",
                  "formatted_free_over_amount": "€99,00"
                },
                "min": {
                  "hours": 72,
                  "days": 3
                },
                "max": {
                  "hours": 120,
                  "days": 5
                }
              },
              {
                "shipping_method": {
                  "name": "Express Delivery",
                  "reference": null,
                  "price_amount_cents": 1200,
                  "free_over_amount_cents": null,
                  "formatted_price_amount": "€12,00",
                  "formatted_free_over_amount": null
                },
                "min": {
                  "hours": 48,
                  "days": 2
                },
                "max": {
                  "hours": 72,
                  "days": 3
                }
              }
            ]
          },
          {
            "quantity": 6,
            "delivery_lead_times": [
              {
                "shipping_method": {
                  "name": "Standard Shipping",
                  "reference": null,
                  "price_amount_cents": 700,
                  "free_over_amount_cents": 9900,
                  "formatted_price_amount": "€7,00",
                  "formatted_free_over_amount": "€99,00"
                },
                "min": {
                  "hours": 96,
                  "days": 4
                },
                "max": {
                  "hours": 144,
                  "days": 6
                }
              },
              {
                "shipping_method": {
                  "name": "Express Delivery",
                  "reference": null,
                  "price_amount_cents": 1200,
                  "free_over_amount_cents": null,
                  "formatted_price_amount": "€12,00",
                  "formatted_free_over_amount": null
                },
                "min": {
                  "hours": 72,
                  "days": 3
                },
                "max": {
                  "hours": 96,
                  "days": 4
                }
              }
            ]
          }
        ]
      },
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "shipping_category": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/shipping_category",
          "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/shipping_category"
        }
      },
      "prices": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/prices",
          "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/prices"
        }
      },
      "stock_items": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/stock_items",
          "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/stock_items"
        }
      },
      "delivery_lead_times": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/delivery_lead_times",
          "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/delivery_lead_times"
        }
      },
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
