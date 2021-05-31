---
description: How to fetch a collection of manual gateways via API
---

# List all manual gateways

To fetch a collection of manual gateways, send a `GET` request to the `/api/manual_gateways` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/manual\_gateways**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of manual gateways:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/manual_gateways/ \
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
      "type": "manual_gateways",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/manual_gateways/xYZkjABcde"
      },
      "attributes": {
        "name": "US payment gateway",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        },
        "require_capture": true
      },
      "relationships": {
        "payment_methods": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/manual_gateways/xYZkjABcde/relationships/payment_methods",
            "related": "https://yourdomain.commercelayer.io/api/manual_gateways/xYZkjABcde/payment_methods"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 manual_gateways (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/manual_gateways?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/manual_gateways?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/manual_gateways?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of manual gateways can be sorted by the following attributes:

* `name`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

