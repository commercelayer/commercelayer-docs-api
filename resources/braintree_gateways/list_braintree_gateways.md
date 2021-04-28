---
description: How to fetch a collection of braintree gateways via API
---

# List all braintree gateways

To fetch a collection of braintree gateways, send a `GET` request to the `/api/braintree_gateways` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/braintree\_gateways**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of braintree gateways:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/braintree_gateways/ \
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
      "type": "braintree_gateways",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/braintree_gateways/xYZkjABcde"
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
        "descriptor_name": "company*productabc1234",
        "descriptor_phone": "3125551212",
        "descriptor_url": "company.com",
        "webhook_endpoint_url": "https://core.commercelayer.co/webhook_callbacks/braintree_gateways/xxxxx"
      },
      "relationships": {
        "payment_methods": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/braintree_gateways/xYZkjABcde/relationships/payment_methods",
            "related": "https://yourdomain.commercelayer.io/api/braintree_gateways/xYZkjABcde/payment_methods"
          }
        },
        "braintree_payments": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/braintree_gateways/xYZkjABcde/relationships/braintree_payments",
            "related": "https://yourdomain.commercelayer.io/api/braintree_gateways/xYZkjABcde/braintree_payments"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 braintree_gateways (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/braintree_gateways?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/braintree_gateways?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/braintree_gateways?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of braintree gateways can be sorted by the following attributes:

* `name`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

