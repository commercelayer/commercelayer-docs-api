---
description: How to create a coupon codes promotion rule via API
---

# Create a coupon codes promotion rule

To create a new coupon codes promotion rule, send a `POST` request to the `/api/coupon_codes_promotion_rules` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain.commercelayer.io**/api/coupon\_codes\_promotion\_rules**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**promotion** | `object` | Required |
| relationships.**coupons** | `array` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new coupon codes promotion rule:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/coupon_codes_promotion_rules \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "coupon_codes_promotion_rules",
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
    "type": "coupon_codes_promotion_rules",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/coupon_codes_promotion_rules/xYZkjABcde"
    },
    "attributes": {
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "promotion": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/coupon_codes_promotion_rules/xYZkjABcde/relationships/promotion",
          "related": "https://yourdomain.commercelayer.io/api/coupon_codes_promotion_rules/xYZkjABcde/promotion"
        }
      },
      "coupons": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/coupon_codes_promotion_rules/xYZkjABcde/relationships/coupons",
          "related": "https://yourdomain.commercelayer.io/api/coupon_codes_promotion_rules/xYZkjABcde/coupons"
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

