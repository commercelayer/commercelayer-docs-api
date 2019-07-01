---
description: How to request the API to return only specific fields
---

# Sparse fieldsets

When you fetch a resource or collection, you can request the API to return only specific fields, using the `fields` query parameter. This reduces the response payload, optimizing the performances.

{% hint style="warning" %}
The value of the `fields` parameter must be a comma-separated list that refers to the name\(s\) of the fields to be returned. Pay attention to avoid whitespaces before or after each comma.
{% endhint %}

### Example

{% tabs %}
{% tab title="Request" %}
The following request fetches an SKU code and name, and the formatted amount of the related prices:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/skus/1234?include=prices&fields[skus]=code,name&fields[prices]=formatted_amount \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning the requested fieldset: 

```javascript
{
  "data": {
    "id": "1234",
    "type": "skus",
    "links": {...},
    "attributes": {
      "code": "TSHIRTMM000000FFFFFFXLXX",
      "name": "Black Men T-shirt with White Logo (XL)"
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
            "id": 1234
          }
        ]
      },
      "stock_items": {
        "links": {...}
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
        "links": {...},
        "attributes": {
          "formatted_amount": "€100,00"
        },
        "relationships": {
          "price_list": {
            "links": {...}
          },
          "sku": {
            "links": {...}
          }
        },
        "meta": {...}
      }
    }
  ]
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
You can request sparse fieldsets also when [creating](creating-resources.md) or [updating](updating-resources.md) resources.
{% endhint %}

