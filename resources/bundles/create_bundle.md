---
description: How to create a bundle via API
---

# Create a bundle

To create a new bundle, send a `POST` request to the `/api/bundles` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/bundles**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**code** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**description** | `string` | Optional |
| attributes.**image_url** | `string` | Optional |
| attributes.**price_amount_cents** | `integer` | Required |
| attributes.**compare_at_amount_cents** | `integer` | Required |
| attributes.**_compute_compare_at_amount** | `boolean, value is 'true'` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**market** | `object` | Required, unless in scope |
| relationships.**sku_list** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new bundle:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/bundles \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "bundles",
    "attributes": {
      "code": "BUNDMM000000FFFFFFXLXX",
      "name": "Black Men T-shirt (XL) with Black Cap and Socks, all with White Logo",
      "price_amount_cents": "10000",
      "compare_at_amount_cents": "13000"
    },
    "relationships": {
      "market": {
        "data": {
          "type": "markets",
          "id": "QWERtyUpBa"
        }
      },
      "sku_list": {
        "data": {
          "type": "sku_lists",
          "id": "QWERtyUpBa"
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
    "type": "bundles",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde"
    },
    "attributes": {
      "code": "BUNDMM000000FFFFFFXLXX",
      "name": "Black Men T-shirt (XL) with Black Cap and Socks, all with White Logo",
      "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
      "image_url": "https://img.yourdomain.com/bundles/xYZkjABcde.png",
      "price_amount_cents": 10000,
      "price_amount_float": 100.0,
      "formatted_price_amount": "€100,00",
      "compare_at_amount_cents": 13000,
      "compare_at_amount_float": 130.0,
      "formatted_compare_at_amount": "€130,00",
      "skus_count": 2,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "market": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde/relationships/market",
          "related": "https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde/market"
        }
      },
      "sku_list": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde/relationships/sku_list",
          "related": "https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde/sku_list"
        }
      },
      "skus": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde/relationships/skus",
          "related": "https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde/skus"
        }
      },
      "attachments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde/relationships/attachments",
          "related": "https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde/attachments"
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

