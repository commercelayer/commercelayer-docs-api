---
description: How to fetch a collection of return line items via API
---

# List all return line items

To fetch a collection of return line items, send a `GET` request to the `/api/return_line_items` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/return_line_items**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of return line items:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/return_line_items/ \
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
      "type": "return_line_items",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/return_line_items/xYZkjABcde"
      },
      "attributes": {
        "sku_code": "TSHIRTMM000000FFFFFFXLXX",
        "name": "Black Men T-shirt with White Logo (XL)",
        "quantity": 4,
        "return_reason": {
          "size": "was wrong"
        },
        "restocked_at": "2018-01-01T12:00:00.000Z",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "return": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/return_line_items/xYZkjABcde/relationships/return",
            "related": "https://yourdomain.commercelayer.io/api/return_line_items/xYZkjABcde/return"
          }
        },
        "line_item": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/return_line_items/xYZkjABcde/relationships/line_item",
            "related": "https://yourdomain.commercelayer.io/api/return_line_items/xYZkjABcde/line_item"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 return_line_items (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/return_line_items?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/return_line_items?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/return_line_items?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of return line items can be sorted by the following attributes:

* `quantity`
* `restocked_at`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

