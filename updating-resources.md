---
description: How to update a resource via API
---

# Updating resources

You can update a resource by sending a `PATCH` request to the resources endpoint, with a JSON payload.

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
The following request updates the description of an existing SKU:

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/skus/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "skus",
    "id": "xYZkjABcde",
    "attributes": {
      "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning the updated resource object:

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
            "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
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

