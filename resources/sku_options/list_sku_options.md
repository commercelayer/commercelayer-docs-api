---
description: How to fetch a collection of SKU options via API
---

# List all SKU options

To fetch a collection of SKU options, send a `GET` request to the `/api/sku_options` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/sku\_options**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of SKU options:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/sku_options/ \
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
      "type": "sku_options",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/sku_options/xYZkjABcde"
      },
      "attributes": {
        "name": "Embossing",
        "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        "price_amount_cents": 1000,
        "price_amount_float": 10.0,
        "formatted_price_amount": "€10,00",
        "delay_hours": 48,
        "delay_days": 2,
        "sku_code_regex": "^(A|B).*$",
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
            "self": "https://yourdomain.commercelayer.io/api/sku_options/xYZkjABcde/relationships/market",
            "related": "https://yourdomain.commercelayer.io/api/sku_options/xYZkjABcde/market"
          }
        },
        "attachments": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/sku_options/xYZkjABcde/relationships/attachments",
            "related": "https://yourdomain.commercelayer.io/api/sku_options/xYZkjABcde/attachments"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 sku_options (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/sku_options?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/sku_options?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/sku_options?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of SKU options can be sorted by the following attributes:

* `name`
* `price_amount_cents`
* `delay_hours`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

