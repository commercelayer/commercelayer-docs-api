---
description: How to request the API to return only specific fields
---

# Sparse fieldsets

When you fetch a resource or collection, you can request the API to return only specific fields, using the `fields` query parameter. This reduces the response payload, optimizing the performances. If you want the API to return also specific related resources data, they must be [included](including-associations.md) and added to the `fields` list as well.

{% hint style="warning" %}
The value of the `fields` parameter must be a comma-separated list that refers to the name\(s\) of the fields to be returned. Pay attention to avoid whitespaces before or after each comma.
{% endhint %}

### Examples

#### Requesting specific attributes only

{% tabs %}
{% tab title="Request" %}
The following request fetches an SKU code and name:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/skus/xYZkjABcde?fields[skus]=code,name \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning the requested fieldset:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "skus",
    "links": {...},
    "attributes": {
        "code": "TSHIRTMM000000FFFFFFXLXX",
        "name": "Black Men T-shirt with White Logo (XL)"
    },
    "meta": {...}
  }
}
```
{% endtab %}
{% endtabs %}

#### Requesting specific related resources

{% tabs %}
{% tab title="Request" %}
The following request fetches an SKU code, name, and related prices plus the formatted amount and the related price lists of each price:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/skus/xYZkjABcde?include=prices,prices.price_list&fields[skus]=code,name,prices&fields[prices]=formatted_amount,price_list \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning the requested fieldset: 

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "skus",
    "links": {...},
    "attributes": {
      "code": "TSHIRTMM000000FFFFFFXLXX",
      "name": "Black Men T-shirt with White Logo (XL)"
    },
    "relationships": {
      "prices": {
        "links": {...},
        "data": [
          {
            "type": "prices",
            "id": "ajKQUMdKQp"
          },
          {
            "type": "prices",
            "id": "AKeQUowyYa"
          }
        ]
      }
    },
    "meta": {...}
  },
  "included": [
    {
      "id": "ajKQUMdKQp",
      "type": "prices",
      "links": {...},
      "attributes": {
        "formatted_amount": "€100,00"
      },
      "relationships": {
        "price_list": {
          "links": {...},
          "data": {
            "type": "price_lists",
            "id": "xlqjNCaKLw"
          }
        }
      },
      "meta": {...}
    },
    {
      "id": "AKeQUowyYa",
      "type": "prices",
      "links": {...},
      "attributes": {
        "formatted_amount": "$124.80"
      },
      "relationships": {
        "price_list": {
          "links": {...},
          "data": {
            "type": "price_lists",
            "id": "vLrWRCJWBE"
          }
        }
      },
      "meta": {...}
    },
    {
      "id": "xlqjNCaKLw",
      "type": "price_lists",
      "links": {...},
      "attributes": {
        "name": "EUR Price List",
        "currency_code": "EUR",
        "tax_included": true,
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": null,
        "reference_origin": null,
        "metadata": {}
      },
      "relationships": {
        "prices": {
          "links": {...}
        },
        "attachments": {
          "links": {...}
        }
      },
      "meta": {...}
    },
    {
      "id": "vLrWRCJWBE",
      "type": "price_lists",
      "links": {...},
      "attributes": {
        "name": "USD Price List",
        "currency_code": "USD",
        "tax_included": false,
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": null,
        "reference_origin": null,
        "metadata": {}
      },
      "relationships": {
          "prices": {
              "links": {...}
          },
          "attachments": {
              "links": {...}
          }
      },
      "meta": {...}
    }
  ]
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
You can request sparse fieldsets also when [creating](creating-resources.md) or [updating](updating-resources.md) resources.
{% endhint %}

