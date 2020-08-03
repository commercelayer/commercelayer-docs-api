---
description: How to fetch a collection of external promotions via API
---

# List all external promotions

To fetch a collection of external promotions, send a `GET` request to the `/api/external_promotions` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/external_promotions**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of external promotions:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/external_promotions/ \
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
    },
    {
      "other": "... 9 external_promotions (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/external_promotions?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/external_promotions?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/external_promotions?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of external promotions can be sorted by the following attributes:

* `name`
* `starts_at`
* `expires_at`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

