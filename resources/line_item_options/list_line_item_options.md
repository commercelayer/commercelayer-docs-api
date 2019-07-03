---
description: How to fetch a collection of line item options via API
---

# List all line item options

To fetch a collection of line item options, send a `GET` request to the `/api/line_item_options` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/line_item_options**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of line item options:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/line_item_options/ \
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
      "type": "line_item_options",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/line_item_options/xYZkjABcde"
      },
      "attributes": {
        "name": "Embossing",
        "quantity": "2",
        "currency_code": "EUR",
        "unit_amount_cents": "990",
        "unit_amount_float": "9.9",
        "formatted_unit_amount": "€9,90",
        "total_amount_cents": "1880",
        "total_amount_float": "18.8",
        "formatted_total_amount": "€18,80",
        "delay_hours": "48",
        "delay_days": "2",
        "options": {
          "embossing_text": "Happy Birthday!"
        },
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANYREFEFERNCE",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "line_item": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/line_item_options/xYZkjABcde/relationships/line_item",
            "related": "https://yourdomain.commercelayer.io/api/line_item_options/xYZkjABcde/line_item"
          }
        },
        "sku_option": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/line_item_options/xYZkjABcde/relationships/sku_option",
            "related": "https://yourdomain.commercelayer.io/api/line_item_options/xYZkjABcde/sku_option"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 line_item_options (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/line_item_options?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/line_item_options?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/line_item_options?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of line item options can be sorted by the following attributes:

* `name`
* `total_amount_cents`
* `delay_hours`
* `id`
* `created_at`
* `updated_at`
* `reference`

{% page-ref page="../../sorting-results.md" %}
