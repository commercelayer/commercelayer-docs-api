---
description: How to create a SKU list promotion rule via API
---

# Create a SKU list promotion rule

To create a new SKU list promotion rule, send a `POST` request to the `/api/sku_list_promotion_rules` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain.commercelayer.io**/api/sku\_list\_promotion\_rules**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| attributes.**all\_skus** | `boolean` | Optional, default is 'false' |
| relationships.**promotion** | `object` | Required |
| relationships.**sku\_list** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new SKU list promotion rule:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/sku_list_promotion_rules \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "sku_list_promotion_rules",
    "relationships": {
      "promotion": {
        "data": {
          "type": "promotions",
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
    "type": "sku_list_promotion_rules",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/sku_list_promotion_rules/xYZkjABcde"
    },
    "attributes": {
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      },
      "all_skus": "true"
    },
    "relationships": {
      "promotion": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/sku_list_promotion_rules/xYZkjABcde/relationships/promotion",
          "related": "https://yourdomain.commercelayer.io/api/sku_list_promotion_rules/xYZkjABcde/promotion"
        }
      },
      "sku_list": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/sku_list_promotion_rules/xYZkjABcde/relationships/sku_list",
          "related": "https://yourdomain.commercelayer.io/api/sku_list_promotion_rules/xYZkjABcde/sku_list"
        }
      },
      "skus": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/sku_list_promotion_rules/xYZkjABcde/relationships/skus",
          "related": "https://yourdomain.commercelayer.io/api/sku_list_promotion_rules/xYZkjABcde/skus"
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

