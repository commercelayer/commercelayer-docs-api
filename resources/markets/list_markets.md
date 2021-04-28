---
description: How to fetch a collection of markets via API
---

# List all markets

To fetch a collection of markets, send a `GET` request to the `/api/markets` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/markets**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of markets:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/markets/ \
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
      "type": "markets",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde"
      },
      "attributes": {
        "number": 1234,
        "name": "EU Market",
        "facebook_pixel_id": "1234567890",
        "checkout_url": "https://checkout.yourbrand.com/:order_id",
        "external_prices_url": "https://external_prices.yourbrand.com",
        "private": true,
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "merchant": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/relationships/merchant",
            "related": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/merchant"
          }
        },
        "price_list": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/relationships/price_list",
            "related": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/price_list"
          }
        },
        "inventory_model": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/relationships/inventory_model",
            "related": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/inventory_model"
          }
        },
        "customer_group": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/relationships/customer_group",
            "related": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/customer_group"
          }
        },
        "attachments": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/relationships/attachments",
            "related": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/attachments"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 markets (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/markets?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/markets?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/markets?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of markets can be sorted by the following attributes:

* `name`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

