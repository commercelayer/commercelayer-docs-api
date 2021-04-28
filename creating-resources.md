---
description: How to create a resource via API
---

# Creating resources

You can create a resource by sending a `POST` request to the resources endpoint, with a JSON payload.

{% hint style="warning" %}
The **Content-Type** header must be `application/vnd.api+json`.
{% endhint %}

{% hint style="info" %}
You can get the list of arguments, with type and examples from the documentation of each resource.
{% endhint %}

{% page-ref page="authentication/" %}

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new SKU:

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
      "code": "TSHIRTMM000000FFFFFFXLXX",
      "name": "Black Men T-shirt with White Logo (XL)"
    },
    "relationships": {
      "shipping_category": {
        "data": {
          "type": "shipping_categories",
          "id": "zxcVBnMASd"
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
            "description": null,
            "image_url": null,
            "tag_names": "",
            "pieces_per_pack": null,
            "weight": null,
            "unit_of_weight": null,
            "hs_tariff_number": null,
            "do_not_ship": false,
            "do_not_track": false,
            "created_at": "2018-01-01T12:00:00.000Z",
            "updated_at": "2018-01-01T12:00:00.000Z",
            "reference": null,
            "metadata": {}
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

