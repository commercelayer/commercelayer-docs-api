---
description: How to update an existing SKU via API
---

# Update a SKU

To update an existing SKU, send a `PATCH` request to the `/api/skus/{{id}}` endpoint, where `id` is the ID of the resource that you want to update. 

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://yourdomain.commercelayer.io**/api/skus/{{id}}**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**code** | `string` | Optional |
| attributes.**name** | `string` | Optional |
| attributes.**description** | `string` | Optional |
| attributes.**image\_url** | `string` | Optional |
| attributes.**tag\_names** | `string` | Optional |
| attributes.**pieces\_per\_pack** | `integer` | Optional |
| attributes.**weight** | `float` | Optional |
| attributes.**unit\_of\_weight** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**shipping\_category** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to update the description e the shipping category of the SKU identified by the ID "1234":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/skus/1234 \
  -H 'Authorization: Bearer your-access-token' \
  -d '{
  "data": {
    "type": "skus",
    "id": 1234,
    "attributes": {
      "description": "Diam phasellus vestibulum lorem sed risus ultricies tristique nulla. Suspendisse ultrices gravida dictum fusce ut placerat orci nulla pellentesque."
    },
    "relationships": {
      "shipping_category": {
    	"data": {
    	  "type": "shipping_categories",
          "id": "1234"
        }
      }
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
    "id": "1234",
    "type": "skus",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/skus/1234"
    },
    "attributes": {
      "code": "TSHIRTMM000000E63E74MXXX",
      "name": "Black Men T-shirt with Pink Logo (M)",
      "description": "Diam phasellus vestibulum lorem sed risus ultricies tristique nulla. Suspendisse ultrices gravida dictum fusce ut placerat orci nulla pellentesque.",
      "image_url": "https://img.yourdomain.io/skus/TSHIRTMM000000E63E74.png?fm=jpg&q=90",
      "tag_names": "",
      "pieces_per_pack": null,
      "weight": null,
      "unit_of_weight": null,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2019-01-01T12:00:00.000Z",
      "reference": "TSHIRTMM000000E63E74",
      "metadata": {}
    },
    "relationships": {
      "shipping_category": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/skus/1234/relationships/shipping_category",
          "related": "https://yourdomain.commercelayer.io/api/skus/1234/shipping_category"
        }
      },
      "prices": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/skus/1234/relationships/prices",
          "related": "https://yourdomain.commercelayer.io/api/skus/1234/prices"
          }
        },
        "stock_items": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/skus/1234/relationships/stock_items",
            "related": "https://yourdomain.commercelayer.io/api/skus/1234/stock_items"
          }
        },
        "delivery_lead_times": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/skus/1234/relationships/delivery_lead_times",
            "related": "https://yourdomain.commercelayer.io/api/skus/1234/delivery_lead_times"
          }
        },
        "sku_options": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/skus/1234/relationships/sku_options",
            "related": "https://yourdomain.commercelayer.io/api/skus/1234/sku_options"
          }
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

