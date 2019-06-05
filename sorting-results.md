---
description: How to request a specific sort for the results of a collection of resources
---

# Sorting results

When you fetch a collection of resources, you can request a specific sort for the results.

{% hint style="info" %}
You can get the full list of sortable attributes from the documentation of each resource.
{% endhint %}

{% api-method method="get" host="https://your-brand.commercelayer.io" path="/api/skus/1234?sort=-created\_at,code" %}
{% api-method-summary %}
Get a collection of resources, sorted by specific parameters
{% endapi-method-summary %}

{% api-method-description %}
This request fetches a collection of SKUs sorted by their creation date \(descending\) and code.
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
On success, the API returns the all the SKUs, sorted by the specific filter parameters.
{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "id": "1234",
        "type": "skus",
        "links": {
            "self": "https://spineless.commercelayer.io/api/skus/1234"
        },
        "attributes": {
            "code": "TSHIRTMM000000E63E74MXXX",
            "name": "Black Men T-shirt with Pink Logo (M)",
            "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam pellentesque in neque vitae tincidunt. In gravida eu ipsum non condimentum. Curabitur libero leo, gravida a dictum vestibulum, sollicitudin vel quam.",
            "image_url": "https://img.commercelayer.io/skus/TSHIRTMM000000E63E74.png?fm=jpg&q=90",
            "tag_names": "",
            "pieces_per_pack": null,
            "weight": null,
            "unit_of_weight": null,
            "inventory": null,
            "created_at": "2019-05-14T10:36:53.711Z",
            "updated_at": "2019-05-14T10:36:53.711Z",
            "reference": "TSHIRTMM000000E63E74",
            "metadata": {}
        },
        "relationships": {
            "shipping_category": {
                "links": {
                    "self": "https://spineless.commercelayer.io/api/skus/1234/relationships/shipping_category",
                    "related": "https://spineless.commercelayer.io/api/skus/1234/shipping_category"
                }
            },
            "prices": {
                "links": {
                    "self": "https://spineless.commercelayer.io/api/skus/1234/relationships/prices",
                    "related": "https://spineless.commercelayer.io/api/skus/1234/prices"
                }
            },
            "stock_items": {
                "links": {
                    "self": "https://spineless.commercelayer.io/api/skus/1234/relationships/stock_items",
                    "related": "https://spineless.commercelayer.io/api/skus/1234/stock_items"
                }
            },
            "delivery_lead_times": {
                "links": {
                    "self": "https://spineless.commercelayer.io/api/skus/1234/relationships/delivery_lead_times",
                    "related": "https://spineless.commercelayer.io/api/skus/1234/delivery_lead_times"
                }
            },
            "sku_options": {
                "links": {
                    "self": "https://spineless.commercelayer.io/api/skus/1234/relationships/sku_options",
                    "related": "https://spineless.commercelayer.io/api/skus/1234/sku_options"
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

{% hint style="warning" %}
The value of the `sort` parameter MUST be a comma-separated list of fields. 
{% endhint %}

{% hint style="info" %}
The sort order for each field is ascending unless prefixed with a `-` \(minus\) in which case it's descending. By default, the API sorts ascending on the `id` of the primary resource.
{% endhint %}

