---
description: How to request the API to return only specific fields
---

# Sparse fieldsets

When you fetch a resource or collection, you can request the API to return only specific fields. This reduces the response payload, optimizing the performances.

{% hint style="info" %}
You can request sparse fieldsets also when creating or updating resources.
{% endhint %}

{% api-method method="get" host="https://your-brand.commercelayer.io" path="/api/skus/1234?include=prices&fields\[skus\]=code,name&fields\[prices\]=formatted\_amount" %}
{% api-method-summary %}
Fetch a resource specific fields only
{% endapi-method-summary %}

{% api-method-description %}
This request fetches an SKU code and name, and the formatted amount of the related prices.
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
On success, the API returns the requested fieldset.
{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="warning" %}
The value of the `fields` parameter MUST be a comma-separated list that refers to the name\(s\) of the fields to be returned.
{% endhint %}

