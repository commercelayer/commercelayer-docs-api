---
description: How to fetch a collection of checkout com gateways via API
---

# List all checkout com gateways

To fetch a collection of checkout com gateways, send a `GET` request to the `/api/checkout_com_gateways` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/checkout\_com\_gateways**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of checkout com gateways:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/checkout_com_gateways/ \
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
      "type": "checkout_com_gateways",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde"
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
        "webhook_endpoint_id": "xxxx-yyyy-zzzz",
        "webhook_endpoint_secret": "xxxx-yyyy-zzzz",
        "webhook_endpoint_url": "https://core.commercelayer.co/webhook_callbacks/checkout_com_gateways/xxxxx"
      },
      "relationships": {
        "payment_methods": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde/relationships/payment_methods",
            "related": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde/payment_methods"
          }
        },
        "checkout_com_payments": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde/relationships/checkout_com_payments",
            "related": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde/checkout_com_payments"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 checkout_com_gateways (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/checkout_com_gateways?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/checkout_com_gateways?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/checkout_com_gateways?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of checkout com gateways can be sorted by the following attributes:

* `name`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

