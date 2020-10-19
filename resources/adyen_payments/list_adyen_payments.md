---
description: How to fetch a collection of adyen payments via API
---

# List all adyen payments

To fetch a collection of adyen payments, send a `GET` request to the `/api/adyen_payments` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/adyen_payments**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of adyen payments:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/adyen_payments/ \
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
      "type": "adyen_payments",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/adyen_payments/xYZkjABcde"
      },
      "attributes": {
        "payment_methods": "See Adyen official documentation",
        "payment_request_data": "See Adyen official documentation",
        "payment_request_details": "See Adyen official documentation",
        "payment_response": "See Adyen official documentation",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "order": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/adyen_payments/xYZkjABcde/relationships/order",
            "related": "https://yourdomain.commercelayer.io/api/adyen_payments/xYZkjABcde/order"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 adyen_payments (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/adyen_payments?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/adyen_payments?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/adyen_payments?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of adyen payments can be sorted by the following attributes:

* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

