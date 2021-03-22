---
description: How to include a resource and its associations in the same request
---

# Including associations

When you fetch a resource or a collection, you can include its associations in the same request, using the `include` query parameter. This reduces the number of roundtrips, optimizing the performances. 

{% hint style="warning" %}
The value of the `include` parameter must be a comma-separated list of relationship paths \([see example](including-associations.md#fetching-an-sku-and-some-of-its-associations)\). Pay attention to avoid whitespaces before or after each comma. 
{% endhint %}

{% hint style="info" %}
A relationship path is a dot-separated list of relationship names \([see example](including-associations.md#using-relationship-paths)\).
{% endhint %}

### Examples

#### Fetching an SKU and some of its associations

{% tabs %}
{% tab title="Request" %}
The following request fetches the SKU identified by the ID "xYZkjABcde" and the related prices and stock items:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/skus/xYZkjABcde?include=prices,stock_items \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: your-access-token' 
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning the resource object and the included associations:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
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
            "id": "yzkWXfgHQS"
          }
        ]
      },
      "stock_items": {
        "links": {...},
        "data": [
          {
            "type": "stock_items",
            "id": "aBmNkPQRst"
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
        "id": "yzkWXfgHQS",
        "type": "prices",
        "links": {...},
        "attributes": {
          "currency_code": "EUR",
          "sku_code": "TSHIRTMM000000FFFFFFXLXX",
          "amount_cents": 10000,
          "amount_float": 100.0,
          "formatted_amount": "€100,00",
          "compare_at_amount_cents": 13000,
          "compare_at_amount_float": 130.0,
          "formatted_compare_at_amount": "€130,00",
          "created_at": "2018-01-01T12:00:00.000Z",
          "updated_at": "2018-01-01T12:00:00.000Z",
          "reference": "ANYREFEFERNCE",
          "metadata": {
            "foo": "bar"
          }
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
      }
    },
    {
      "data": {
        "id": "aBmNkPQRst",
        "type": "stock_items",
        "links": {...},
        "attributes": {
          "sku_code": "TSHIRTMM000000FFFFFFXLXX",
          "quantity": 100,
          "created_at": "2018-01-01T12:00:00.000Z",
          "updated_at": "2018-01-01T12:00:00.000Z",
          "reference": "ANYREFEFERNCE",
          "metadata": {
            "foo": "bar"
          }
        },
        "relationships": {
          "stock_location": {
            "links": {...}
          },
          "sku": {
            "links": {...}
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
{% endtab %}
{% endtabs %}

#### Using relationship paths

{% tabs %}
{% tab title="Request" %}
The following request features the relationship path `prices.price_list` as the value of the include parameter, where `prices` is a relationship listed under an SKU resource object, and `price_list` is a relationship listed under a price resource object:

```javascript
curl -X GET \
  http://yourdomain.commercelayer.io/api/skus/xYZkjABcde?include=prices.price_list \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning the resource object and the included associations:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "skus",
    "links": {...},
    "attributes": {
      "code": "TSHIRTMM000000FFFFFFMXXX",
      "name": "Black Men T-shirt with White Logo (M)",
      "description": "Diam phasellus vestibulum lorem sed risus ultricies tristique nulla. Suspendisse ultrices gravida dictum fusce ut placerat orci nulla pellentesque.",
      "image_url": "https://img.yourdomain.com/skus/xYZkjABcde.png",
      "tag_names": "",
      "pieces_per_pack": null,
      "weight": null,
      "unit_of_weight": null,
      "inventory": null,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {}
    },
    "relationships": {
      "shipping_category": {
        "links": {...}
      },
      "prices": {
        "links": {...},
        "data": [
          {
            "type": "prices",
            "id": "yzkWXfgHQS"
          },
          {
            "type": "prices",
            "id": "WAspXYhfCV"
          },
        ]
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
  "included": [
    {
      "id": "yzkWXfgHQS",
      "type": "prices",
      "links": {...},
      "attributes": {
        "currency_code": "USD",
        "sku_code": "TSHIRTMM000000FFFFFFMXXX",
        "amount_cents": 3480,
        "amount_float": 34.8,
        "formatted_amount": "$34.80",
        "compare_at_amount_cents": 4524,
        "compare_at_amount_float": 45.24,
        "formatted_compare_at_amount": "$45.24",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": null,
        "metadata": {}
      },
      "relationships": {
        "price_list": {
          "links": {...},
          "data": {
            "type": "price_lists",
            "id": "QWERtyUpBa"
          }
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
      "id": "WAspXYhfCV",
      "type": "prices",
      "links": {...},
      "attributes": {
        "currency_code": "EUR",
        "sku_code": "TSHIRTMM000000FFFFFFMXXX",
        "amount_cents": 4900,
        "amount_float": 49.0,
        "formatted_amount": "€49,00",
        "compare_at_amount_cents": 4900,
        "compare_at_amount_float": 49.0,
        "formatted_compare_at_amount": "€49,00",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": null,
        "metadata": {}
      },
      "relationships": {
        "price_list": {
          "links": {...},
          "data": {
            "type": "price_lists",
            "id": "saDFGhjkLZ"
          }
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
      "id": "QWERtyUpBa",
      "type": "price_lists",
      "links": {...},
      "attributes": {
        "name": "USD Price List",
        "currency_code": "USD",
        "tax_included": false,
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": null,
        "metadata": {}
      },
      "relationships": {
        "prices": {
          "links": {...}
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "id": "saDFGhjkLZ",
      "type": "price_lists",
      "links": {...},
      "attributes": {
        "name": "EUR Price List",
        "currency_code": "EUR",
        "tax_included": true,
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": null,
        "metadata": {}
      },
      "relationships": {
        "prices": {
          "links": {...}
        }
      },
      "meta": {
        "mode": "test"
      }
    }
  ]
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
You can request to include associations also when [creating](creating-resources.md) or [updating](updating-resources.md) resources.
{% endhint %}

