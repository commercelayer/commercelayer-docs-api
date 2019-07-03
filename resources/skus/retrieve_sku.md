---
description: How to fetch a specific SKU via API
---

# Retrieve an SKU

To fetch a single SKU, send a `GET` request to the `/api/skus/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/skus/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the SKU identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/skus/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

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
      "image_url": "https://img.yourbrand.com/skus/xYZkjABcde.png",
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
          "self": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/relationships/shipping_category",
          "related": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/shipping_category"
        }
      },
      "prices": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/relationships/prices",
          "related": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/prices"
        }
      },
      "stock_items": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/relationships/stock_items",
          "related": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/stock_items"
        }
      },
      "delivery_lead_times": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/relationships/delivery_lead_times",
          "related": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/delivery_lead_times"
        }
      },
      "sku_options": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/relationships/sku_options",
          "related": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/sku_options"
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

