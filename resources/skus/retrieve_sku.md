---
description: How to fetch a specific SKU via API
---

# Retrieve a SKU

To fetch a single SKU, send a `GET` request to the `/api/skus/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/skus/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the SKU identified by the id "xYZkjABcde":

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
    "links": {
      "self": "https://yourdomein.commercelayer.io/api/skus/xYZkjABcde"
    },
    "attributes": {
      "code": "TSHIRTMM000000FFFFFFXLXX"
      "name": "Black Men T-shirt with White Logo (XL)"
      "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
      "image_url": "https://img.yourbrand.com/skus/1234.png"
      "tag_names": "Men, Black, XL"
      "pieces_per_pack": "6"
      "weight": "300"
      "unit_of_weight": "gr"
      "created_at": "2018-01-01T12:00:00.000Z"
      "updated_at": "2018-01-01T12:00:00.000Z"
      "reference": "ANYREFEFERNCE"
      "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
      "shipping_category": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/shipping_category",
            "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/shipping_category"
        }
      }
      "prices": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/prices",
            "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/prices"
        }
      }
      "stock_items": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/stock_items",
            "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/stock_items"
        }
      }
      "delivery_lead_times": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/delivery_lead_times",
            "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/delivery_lead_times"
        }
      }
      "sku_options": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/sku_options",
            "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/sku_options"
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
