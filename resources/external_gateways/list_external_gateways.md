---
description: How to fetch a collection of external gateways via API
---

# List all external gateways

To fetch a collection of external gateways, send a `GET` request to the `/api/external_gateways` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/external\_gateways**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of external gateways:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/external_gateways/ \
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
      "type": "external_gateways",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/external_gateways/xYZkjABcde"
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
        "shared_secret": "xxxx-yyyy-zzzz",
        "authorize_url": "https://external_gateway.com/authorize",
        "capture_url": "https://external_gateway.com/capture",
        "void_url": "https://external_gateway.com/void",
        "refund_url": "https://external_gateway.com/refund"
      },
      "relationships": {
        "payment_methods": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/external_gateways/xYZkjABcde/relationships/payment_methods",
            "related": "https://yourdomain.commercelayer.io/api/external_gateways/xYZkjABcde/payment_methods"
          }
        },
        "external_payments": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/external_gateways/xYZkjABcde/relationships/external_payments",
            "related": "https://yourdomain.commercelayer.io/api/external_gateways/xYZkjABcde/external_payments"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 external_gateways (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/external_gateways?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/external_gateways?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/external_gateways?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of external gateways can be sorted by the following attributes:

* `name`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

