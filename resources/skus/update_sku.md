---
description: How to update an existing SKU via API
---

# Update an SKU

To update an existing SKU, send a `PATCH` request to the `/api/skus/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://yourdomain.commercelayer.io**/api/skus/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**code** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**description** | `string` | Optional |
| attributes.**image\_url** | `string` | Optional |
| attributes.**tag\_names** | `string` | Optional |
| attributes.**pieces\_per\_pack** | `integer` | Optional |
| attributes.**weight** | `float` | Optional |
| attributes.**unit\_of\_weight** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**shipping\_category** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the SKU identified by the ID "xYZkjABcde":

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
      "code": "TSHIRTMM000000FFFFFFXLXX"
      "name": "Black Men T-shirt with White Logo (XL)"
      "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
      "image_url": "https://img.yourbrand.com/skus/xYZkjABcde.png"
      "tag_names": "Men, Black, XL"
      "pieces_per_pack": "6"
      "weight": "300"
      "unit_of_weight": "gr"
      "reference": "ANYREFEFERNCE"
      "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
      "shipping_category": {
        "data": {
          "type": "shipping_categories",
          "id": "QWERtyUpBa"
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
    "id": "xYZkjABcde",
    "type": "skus",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde"
    },
    "attributes": {
      "code": "TSHIRTMM000000FFFFFFXLXX",
      "name": "Black Men T-shirt with White Logo (XL)",
      "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
      "image_url": "https://img.yourbrand.com/skus/xYZkjABcde.png",
      "tag_names": "Men, Black, XL",
      "pieces_per_pack": "6",
      "weight": "300",
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
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/relationships/shipping_category",
          "related": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/shipping_category"
        }
      },
      "prices": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/relationships/prices",
          "related": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/prices"
        }
      },
      "stock_items": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/relationships/stock_items",
          "related": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/stock_items"
        }
      },
      "delivery_lead_times": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/relationships/delivery_lead_times",
          "related": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/delivery_lead_times"
        }
      },
      "sku_options": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/relationships/sku_options",
          "related": "https://{{subdomain}}.commercelayer.io/api/skus/{{sku_id}}/sku_options"
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

