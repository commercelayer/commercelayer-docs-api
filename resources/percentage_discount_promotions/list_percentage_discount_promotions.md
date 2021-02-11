---
description: How to fetch a collection of percentage discount promotions via API
---

# List all percentage discount promotions

To fetch a collection of percentage discount promotions, send a `GET` request to the `/api/percentage_discount_promotions` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/percentage_discount_promotions**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of percentage discount promotions:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/percentage_discount_promotions/ \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a paginated collection of resource objects:

```javascript
{
  "data": [
    {
      "id": "xYZkjABcde",
      "type": "percentage_discount_promotions",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions/xYZkjABcde"
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
        "percentage": "10"
      },
      "relationships": {
        "market": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions/xYZkjABcde/relationships/market",
            "related": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions/xYZkjABcde/market"
          }
        },
        "promotion_rules": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions/xYZkjABcde/relationships/promotion_rules",
            "related": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions/xYZkjABcde/promotion_rules"
          }
        },
        "order_amount_promotion_rule": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions/xYZkjABcde/relationships/order_amount_promotion_rule",
            "related": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions/xYZkjABcde/order_amount_promotion_rule"
          }
        },
        "sku_list_promotion_rule": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions/xYZkjABcde/relationships/sku_list_promotion_rule",
            "related": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions/xYZkjABcde/sku_list_promotion_rule"
          }
        },
        "coupon_codes_promotion_rule": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions/xYZkjABcde/relationships/coupon_codes_promotion_rule",
            "related": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions/xYZkjABcde/coupon_codes_promotion_rule"
          }
        },
        "attachments": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions/xYZkjABcde/relationships/attachments",
            "related": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions/xYZkjABcde/attachments"
          }
        },
        "sku_list": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions/xYZkjABcde/relationships/sku_list",
            "related": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions/xYZkjABcde/sku_list"
          }
        },
        "skus": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions/xYZkjABcde/relationships/skus",
            "related": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions/xYZkjABcde/skus"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 percentage_discount_promotions (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/percentage_discount_promotions?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of percentage discount promotions can be sorted by the following attributes:

* `name`
* `starts_at`
* `expires_at`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

