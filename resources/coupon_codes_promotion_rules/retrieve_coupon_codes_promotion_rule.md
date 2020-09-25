---
description: How to fetch a specific coupon codes promotion rule via API
---

# Retrieve a coupon codes promotion rule

To fetch a single coupon codes promotion rule, send a `GET` request to the `/api/coupon_codes_promotion_rules/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/coupon\_codes\_promotion\_rules/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the coupon codes promotion rule identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/coupon_codes_promotion_rules/xYZkjABcde \
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

