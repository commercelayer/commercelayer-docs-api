---
description: How to fetch a collection of prices via API
---

# List all prices

To fetch a collection of prices, send a `GET` request to the `/api/prices` endpoint.

## Request

**GET** https://yourdomain.commercelayer.io**/api/prices**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of prices:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/prices/ \
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
      "type": "prices",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde"
      },
      "attributes": {
        "currency_code": "EUR",
        "sku_code": "TSHIRTMM000000FFFFFFXLXX",
        "amount_cents": 10000,
        "amount_float": 100.0,
        "formatted_amount": "€100,00",
        "compare_at_amount_cents": 13000,
        "compare_at_amount_float": 130.0,
        "formatted_compare_at_amount": "€130,00",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "price_list": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde/relationships/price_list",
            "related": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde/price_list"
          }
        },
        "sku": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde/relationships/sku",
            "related": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde/sku"
          }
        },
        "attachments": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde/relationships/attachments",
            "related": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde/attachments"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 prices (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/prices?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/prices?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/prices?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

### Sortable attributes

The list of prices can be sorted by the following attributes:

* `amount_cents`
* `compare_at_amount_cents`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

