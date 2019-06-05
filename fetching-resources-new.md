---
description: How to fetch single resources or collections
---

# Fetching resources \[ NEW \]

You can fetch either single resources or collections by sending `GET` requests to the resource endpoints. 

{% api-method method="get" host="https://your-brand.commercelayer.io" path="/api/skus/1234" %}
{% api-method-summary %}
Fetch a single resource
{% endapi-method-summary %}

{% api-method-description %}
This request fetches a single SKU, identified by the ID "1234".
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
On success, the API returns a single resource object.
{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "id": "1234",
    "type": "skus",
    "links": {
      "self": "https://your-brand.commercelayer.io/api/skus/1234"
    },
    "attributes": {
      "code": "TSHIRTMM000000FFFFFFXLXX",
      "name": "Black Men T-shirt with White Logo (XL)",
      "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
      "image_url": "https://img.yourbrand.com/skus/1234.png",
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
      "id": "1234",
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
          "self": "https://your-brand.commercelayer.io/api/skus/1234/relationships/shipping_category",
          "related": "https://your-brand.commercelayer.io/api/skus/1234/shipping_category"
        }
      },
      "prices": {
        "links": {
          "self": "https://your-brand.commercelayer.io/api/skus/1234/relationships/prices",
          "related": "https://your-brand.commercelayer.io/api/skus/1234/prices"
        }
      },
      "stock_items": {
        "links": {
          "self": "https://your-brand.commercelayer.io/api/skus/1234/relationships/stock_items",
          "related": "https://your-brand.commercelayer.io/api/skus/1234/stock_items"
        }
      },
      "delivery_lead_times": {
        "links": {
          "self": "https://your-brand.commercelayer.io/api/skus/1234/relationships/delivery_lead_times",
          "related": "https://your-brand.commercelayer.io/api/skus/1234/delivery_lead_times"
        }
      },
      "sku_options": {
        "links": {
          "self": "https://your-brand.commercelayer.io/api/skus/1234/relationships/sku_options",
          "related": "https://your-brand.commercelayer.io/api/skus/1234/sku_options"
        }
      }
    },
    "meta": {
      "mode": "test"
    }
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://your-brand.commercelayer.io" path="/api/skus/" %}
{% api-method-summary %}
Fetch a collection of resources
{% endapi-method-summary %}

{% api-method-description %}
This request fetches the entire collection of SKUs.
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
On success, the API returns a paginated collection of SKUs.
{% endapi-method-response-example-description %}

```javascript
{
  "data": [
    {
      "id": "1234",
      "type": "skus",
      "links": {
        "self": "https://your-brand.commercelayer.io/api/skus/1234"
      },
      "attributes": {
        "code": "TSHIRTMM000000FFFFFFXLXX",
        "name": "Black Men T-shirt with White Logo (XL)",
        "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        "image_url": "https://img.yourbrand.com/skus/1234.png",
        "tag_names": "Men, Black, XL",
        "pieces_per_pack": "6",
        "weight": "300",
        "unit_of_weight": "gr",
        "id": "1234",
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
            "self": "https://your-brand.commercelayer.io/api/skus/1234/relationships/shipping_category",
            "related": "https://your-brand.commercelayer.io/api/skus/1234/shipping_category"
          }
        },
        "prices": {
          "links": {
            "self": "https://your-brand.commercelayer.io/api/skus/1234/relationships/prices",
            "related": "https://your-brand.commercelayer.io/api/skus/1234/prices"
          }
        },
        "stock_items": {
          "links": {
            "self": "https://your-brand.commercelayer.io/api/skus/1234/relationships/stock_items",
            "related": "https://your-brand.commercelayer.io/api/skus/1234/stock_items"
          }
        },
        "delivery_lead_times": {
          "links": {
            "self": "https://your-brand.commercelayer.io/api/skus/1234/relationships/delivery_lead_times",
            "related": "https://your-brand.commercelayer.io/api/skus/1234/delivery_lead_times"
          }
        },
        "sku_options": {
          "links": {
            "self": "https://your-brand.commercelayer.io/api/skus/1234/relationships/sku_options",
            "related": "https://your-brand.commercelayer.io/api/skus/1234/sku_options"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 24 skus (first page)"
    }
  ],
  "meta": {
    "record_count": 125,
    "page_count": 5
  },
  "links": {
    "first": "/api/skus?page[number]=1&page[size]=25",
    "prev": "/api/skus?page[number]=2&page[size]=25",
    "next": "/api/skus?page[number]=4&page[size]=25",
    "last": "/api/skus?page[number]=5&page[size]=25"
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
You can also fetch related resources by sending a `GET` request to the "related" link.
{% endhint %}

{% api-method method="get" host="https://your-brand.commercelayer.io" path="/api/skus/1234/prices" %}
{% api-method-summary %}
Fetch a related resource
{% endapi-method-summary %}

{% api-method-description %}
This request fetches all the prices related to the SKU identified by the ID "1234".
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
On success, the API returns a paginated collection of prices.
{% endapi-method-response-example-description %}

```javascript
{
    "data": [
        {
            "id": "102728",
            "type": "prices",
            "links": {
                "self": "https://your-brand.commercelayer.io/api/prices/102728"
            },
            "attributes": {
                "currency_code": "EUR",
                "sku_code": "TSHIRTMM000000E63E74MXXX",
                "amount_cents": 2900,
                "amount_float": 29,
                "formatted_amount": "€29,00",
                "compare_at_amount_cents": 3770,
                "compare_at_amount_float": 37.7,
                "formatted_compare_at_amount": "€37,70",
                "created_at": "2019-05-14T10:36:53.749Z",
                "updated_at": "2019-05-14T10:36:53.749Z",
                "reference": null,
                "metadata": {}
            },
            "relationships": {
                "price_list": {
                    "links": {
                        "self": "https://your-brand.commercelayer.io/api/prices/102728/relationships/price_list",
                        "related": "https://your-brand.commercelayer.io/api/prices/102728/price_list"
                    }
                },
                "sku": {
                    "links": {
                        "self": "https://your-brand.commercelayer.io/api/prices/102728/relationships/sku",
                        "related": "https://your-brand.commercelayer.io/api/prices/102728/sku"
                    }
                }
            },
            "meta": {
                "mode": "test"
            }
        },
        {
            "id": "102729",
            "type": "prices",
            "links": {
                "self": "https://your-brand.commercelayer.io/api/prices/102729"
            },
            "attributes": {
                "currency_code": "USD",
                "sku_code": "TSHIRTMM000000E63E74MXXX",
                "amount_cents": 3480,
                "amount_float": 34.8,
                "formatted_amount": "$34.80",
                "compare_at_amount_cents": 4524,
                "compare_at_amount_float": 45.24,
                "formatted_compare_at_amount": "$45.24",
                "created_at": "2019-05-14T10:36:53.800Z",
                "updated_at": "2019-05-14T10:36:53.800Z",
                "reference": null,
                "metadata": {}
            },
            "relationships": {
                "price_list": {
                    "links": {
                        "self": "https://your-brand.commercelayer.io/api/prices/102729/relationships/price_list",
                        "related": "https://your-brand.commercelayer.io/api/prices/102729/price_list"
                    }
                },
                "sku": {
                    "links": {
                        "self": "https://your-brand.commercelayer.io/api/prices/102729/relationships/sku",
                        "related": "https://your-brand.commercelayer.io/api/prices/102729/sku"
                    }
                }
            },
            "meta": {
                "mode": "test"
            }
        }
    ],
    "meta": {
        "record_count": 2,
        "page_count": 1
    },
    "links": {
        "first": "https://your-brand.commercelayer.io/api/skus/1234/prices?page%5Bnumber%5D=1&page%5Bsize%5D=25",
        "last": "https://your-brand.commercelayer.io/api/skus/1234/prices?page%5Bnumber%5D=1&page%5Bsize%5D=25"
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

