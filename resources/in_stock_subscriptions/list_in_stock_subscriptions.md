---
description: How to fetch a collection of in stock subscriptions via API
---

# List all in stock subscriptions

To fetch a collection of in stock subscriptions, send a `GET` request to the `/api/in_stock_subscriptions` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/in_stock_subscriptions**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of in stock subscriptions:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/in_stock_subscriptions/ \
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
      "type": "in_stock_subscriptions",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/in_stock_subscriptions/xYZkjABcde"
      },
      "attributes": {
        "status": "active",
        "customer_email": "john@example.com",
        "sku_code": "TSHIRTMM000000FFFFFFXLXX",
        "stock_threshold": 3,
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
            "self": "https://yourdomain.commercelayer.io/api/in_stock_subscriptions/xYZkjABcde/relationships/market",
            "related": "https://yourdomain.commercelayer.io/api/in_stock_subscriptions/xYZkjABcde/market"
          }
        },
        "customer": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/in_stock_subscriptions/xYZkjABcde/relationships/customer",
            "related": "https://yourdomain.commercelayer.io/api/in_stock_subscriptions/xYZkjABcde/customer"
          }
        },
        "sku": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/in_stock_subscriptions/xYZkjABcde/relationships/sku",
            "related": "https://yourdomain.commercelayer.io/api/in_stock_subscriptions/xYZkjABcde/sku"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 in_stock_subscriptions (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/in_stock_subscriptions?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/in_stock_subscriptions?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/in_stock_subscriptions?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of in stock subscriptions can be sorted by the following attributes:

* `status`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

