---
description: How to fetch single resources or collections
---

# Fetching resources

You can fetch either single resources or collections by sending `GET` requests to the resource endpoints. 

{% hint style="warning" %}
The **Accept** header must be `application/vnd.api+json`.
{% endhint %}

{% page-ref page="authentication/" %}

### **Examples**

#### **Fetching a single SKU**

{% tabs %}
{% tab title="Request" %}
The following request fetches a single SKU, the one identified by the ID "xYZkjABcde":

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
    "links": {...},
    "attributes": {
      "code": "TSHIRTMM000000FFFFFFXLXX",
      "name": "Black Men T-shirt with White Logo (XL)",
      "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
      "image_url": "https://img.yourdomain.com/skus/xYZkjABcde.png",
      "tag_names": "Men, Black, XL",
      "pieces_per_pack": 6,
      "weight": 300.0,
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
        "links": {...}
      },
      "prices": {
        "links": {...}
      },
      "stock_items": {
        "links": {...}
      },
      "delivery_lead_times": {
        "links": {...}
      },
      "sku_options": {
        "links": {...}
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

#### **Fetching a collection of SKUs**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of SKUs:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/skus \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' 
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a paginated collection ****of the resource objects:

```javascript
{
  "data": [
    {
      "id": "xYZkjABcde",
      "type": "skus",
      "links": {...},
      "attributes": {
        "code": "TSHIRTMM000000FFFFFFXLXX",
        "name": "Black Men T-shirt with White Logo (XL)",
        "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        "image_url": "https://img.yourdomain.com/skus/xYZkjABcde.png",
        "tag_names": "Men, Black, XL",
        "pieces_per_pack": 6,
        "weight": 300.0,
        "unit_of_weight": "gr",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANYREFEFERNCE",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "shipping_category": {
          "links": {...}
        },
        "prices": {
          "links": {...}
        },
        "stock_items": {
          "links": {...}
        },
        "delivery_lead_times": {
          "links": {...}
        },
        "sku_options": {
          "links": {...}
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 skus (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/skus?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/skus?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/skus?page[number]=14&page[size]=10"
  }
}
```

{% page-ref page="pagination.md" %}
{% endtab %}
{% endtabs %}

#### Fetching related resources

You can also fetch related resources by sending a `GET` request to the "related" link.

{% tabs %}
{% tab title="Request" %}
The following request fetches the prices of the SKU identified by the ID "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/prices \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a paginated collection ****of the related resource objects:

```javascript
{
  "data": [
    {
      "id": "yzkWXfgHQS",
      "type": "prices",
      "links": {...},
      "attributes": {
        "currency_code": "EUR",
        "sku_code": "TSHIRTMM000000FFFFFFMXXX",
        "amount_cents": 4900,
        "amount_float": 49,
        "formatted_amount": "€49,00",
        "compare_at_amount_cents": 4900,
        "compare_at_amount_float": 49,
        "formatted_compare_at_amount": "€49,00",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": null,
        "metadata": {}
      },
      "relationships": {
        "price_list": {
          "links": {...}
        },
        "sku": {
          "links": {...}
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 2 prices (first page)"
    }
  ],
  "meta": {
    "record_count": 3,
    "page_count": 1
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/prices?page[number]=1&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/prices?page[number]=1&page[size]=10"
  }
}
```

{% page-ref page="pagination.md" %}
{% endtab %}
{% endtabs %}

