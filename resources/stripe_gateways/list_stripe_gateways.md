---
description: How to fetch a collection of stripe gateways via API
---

# List all stripe gateways

To fetch a collection of stripe gateways, send a `GET` request to the `/api/stripe_gateways` endpoint.

## Request

**GET** https://yourdomain.commercelayer.io**/api/stripe\_gateways**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of stripe gateways:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/stripe_gateways/ \
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
      "type": "stripe_gateways",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/stripe_gateways/xYZkjABcde"
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
        "webhook_endpoint_url": "https://core.commercelayer.co/webhook_callbacks/stripe_gateways/xxxxx"
      },
      "relationships": {
        "payment_methods": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/stripe_gateways/xYZkjABcde/relationships/payment_methods",
            "related": "https://yourdomain.commercelayer.io/api/stripe_gateways/xYZkjABcde/payment_methods"
          }
        },
        "stripe_payments": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/stripe_gateways/xYZkjABcde/relationships/stripe_payments",
            "related": "https://yourdomain.commercelayer.io/api/stripe_gateways/xYZkjABcde/stripe_payments"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 stripe_gateways (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/stripe_gateways?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/stripe_gateways?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/stripe_gateways?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

### Sortable attributes

The list of stripe gateways can be sorted by the following attributes:

* `name`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

