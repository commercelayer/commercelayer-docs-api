---
description: How to include a resource and its associations in the same request
---

# Including associations

When you fetch a resource or a collection, you can include its associations in the same request. This reduces the number of roundtrips, optimizing the performances.

{% api-method method="get" host="https://your-brand.commercelayer.io" path="/api/skus/1234?include=prices,stock\_items" %}
{% api-method-summary %}
Fetch a resource and its associations
{% endapi-method-summary %}

{% api-method-description %}
This request fetches a single SKU and the related prices and stock items.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
`Bearer {{access_token}}`
{% endapi-method-parameter %}

{% api-method-parameter name="Accept" type="string" required=false %}
`application/vnd.api+json`
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
On success, the API returns the resource object and the included associations.
{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "id": "1234",
    "type": "skus",
    "links": {...},
    "attributes": {...},
    "relationships": {
      "shipping_category": {
        "links": {...}
      },
      "prices": {
        "links": {...},
        "data": [
          {
            "type": "prices",
            "id": 1234
          }
        ]
      },
      "stock_items": {
        "links": {...},
        "data": [
          {
            "type": "stock_items",
            "id": 1234
          }
        ]
      },
      "delivery_lead_times": {
        "links": {...}
      }
    },
    "meta": {
      "mode": "test"
    }
  },
  "included": [
    {
      "data": {
        "id": "1234",
        "type": "prices",
        "links": {
          "self": "https://your-brand.commercelayer.io/api/prices/1234"
        },
        "attributes": {
          "currency_code": "EUR",
          "sku_code": "TSHIRTMM000000FFFFFFXLXX",
          "amount_cents": "10000",
          "amount_float": "100.0",
          "formatted_amount": "€100,00",
          "compare_at_amount_cents": "13000",
          "compare_at_amount_float": "130.00",
          "formatted_compare_at_amount": "€130,00",
          "id": "1234",
          "created_at": "2018-01-01T12:00:00.000Z",
          "updated_at": "2018-01-01T12:00:00.000Z",
          "reference": "ANYREFEFERNCE",
          "metadata": {
            "foo": "bar"
          }
        },
        "relationships": {
          "price_list": {
            "links": {
              "self": "https://your-brand.commercelayer.io/api/prices/1234/relationships/price_list",
              "related": "https://your-brand.commercelayer.io/api/prices/1234/price_list"
            }
          },
          "sku": {
            "links": {
              "self": "https://your-brand.commercelayer.io/api/prices/1234/relationships/sku",
              "related": "https://your-brand.commercelayer.io/api/prices/1234/sku"
            }
          }
        },
        "meta": {
          "mode": "test"
        }
      }
    },
    {
      "data": {
        "id": "1234",
        "type": "stock_items",
        "links": {
          "self": "https://your-brand.commercelayer.io/api/stock_items/1234"
        },
        "attributes": {
          "sku_code": "TSHIRTMM000000FFFFFFXLXX",
          "quantity": "100",
          "id": "1234",
          "created_at": "2018-01-01T12:00:00.000Z",
          "updated_at": "2018-01-01T12:00:00.000Z",
          "reference": "ANYREFEFERNCE",
          "metadata": {
            "foo": "bar"
          }
        },
        "relationships": {
          "stock_location": {
            "links": {
              "self": "https://your-brand.commercelayer.io/api/stock_items/1234/relationships/stock_location",
              "related": "https://your-brand.commercelayer.io/api/stock_items/1234/stock_location"
            }
          },
          "sku": {
            "links": {
              "self": "https://your-brand.commercelayer.io/api/stock_items/1234/relationships/sku",
              "related": "https://your-brand.commercelayer.io/api/stock_items/1234/sku"
            }
          }
        },
        "meta": {
          "mode": "test"
        }
      }
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="warning" %}
The value of the `include` parameter MUST be a comma-separated list of relationship paths.
{% endhint %}

{% hint style="info" %}
A relationship path is a dot-separated list of relationship names. For example, a relationship path could be `prices.price_list` where prices is a relationship listed under an SKU resource object, and price\_list is a relationship listed under a price resource object.
{% endhint %}

