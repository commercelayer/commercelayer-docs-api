---
description: How to update an existing external promotion via API
---

# Update an external promotion

To update an existing external promotion, send a `PATCH` request to the `/api/external_promotions/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/external_promotions/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**name** | `string` | Optional |
| attributes.**starts_at** | `datetime` | Optional |
| attributes.**expires_at** | `datetime` | Optional |
| attributes.**total_usage_limit** | `integer` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| attributes.**promotion_url** | `string` | Optional |
| relationships.**market** | `object` | Optional |
| relationships.**promotion_rules** | `array` | Optional |
| relationships.**order_amount_promotion_rule** | `object` | Optional |
| relationships.**sku_list_promotion_rule** | `object` | Optional |
| relationships.**coupon_codes_promotion_rule** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the external promotion identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/external_promotions/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "external_promotions",
    "id": "xYZkjABcde",
    "attributes": {
      "reference": "ANY-EXTERNAL-REFEFERNCE"
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
    "type": "external_promotions",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/external_promotions/xYZkjABcde"
    },
    "attributes": {
      "name": "Personal promotion",
      "starts_at": "2018-01-01T12:00:00.000Z",
      "expires_at": "2018-01-02T12:00:00.000Z",
      "total_usage_limit": "5",
      "total_usage_count": "2",
      "active": "true",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      },
      "promotion_url": "https://external_promotion.yourbrand.com"
    },
    "relationships": {
      "market": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/external_promotions/xYZkjABcde/relationships/market",
          "related": "https://yourdomain.commercelayer.io/api/external_promotions/xYZkjABcde/market"
        }
      },
      "promotion_rules": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/external_promotions/xYZkjABcde/relationships/promotion_rules",
          "related": "https://yourdomain.commercelayer.io/api/external_promotions/xYZkjABcde/promotion_rules"
        }
      },
      "order_amount_promotion_rule": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/external_promotions/xYZkjABcde/relationships/order_amount_promotion_rule",
          "related": "https://yourdomain.commercelayer.io/api/external_promotions/xYZkjABcde/order_amount_promotion_rule"
        }
      },
      "sku_list_promotion_rule": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/external_promotions/xYZkjABcde/relationships/sku_list_promotion_rule",
          "related": "https://yourdomain.commercelayer.io/api/external_promotions/xYZkjABcde/sku_list_promotion_rule"
        }
      },
      "coupon_codes_promotion_rule": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/external_promotions/xYZkjABcde/relationships/coupon_codes_promotion_rule",
          "related": "https://yourdomain.commercelayer.io/api/external_promotions/xYZkjABcde/coupon_codes_promotion_rule"
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

