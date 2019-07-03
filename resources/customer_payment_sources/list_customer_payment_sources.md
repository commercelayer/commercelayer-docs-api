---
description: How to fetch a collection of customer payment sources via API
---

# List all customer payment sources

To fetch a collection of customer payment sources, send a `GET` request to the `/api/customer_payment_sources` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/customer_payment_sources**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of customer payment sources:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/customer_payment_sources/ \
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
      "type": "customer_payment_sources",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/customer_payment_sources/xYZkjABcde"
      },
      "attributes": {
        "name": "XXXX-XXXX-XXXX-1111"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
      },
      "relationships": {
        "customer": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/customer_payment_sources/xYZkjABcde/relationships/customer",
              "related": "https://yourdomain.commercelayer.io/api/customer_payment_sources/xYZkjABcde/customer"
          }
        }
        "payment_source": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/customer_payment_sources/xYZkjABcde/relationships/payment_source",
              "related": "https://yourdomain.commercelayer.io/api/customer_payment_sources/xYZkjABcde/payment_source"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 customer payment sources (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/customer_payment_sources?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/customer_payment_sources?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/customer_payment_sources?page[number]=14&page[size]=10"
  }
}
```

{% page-ref page="../../pagination.md" %}
{% endtab %}
{% endtabs %}

### Sortable attributes

The list of customer payment sources can be sorted by the following attributes:

* `id`
* `created_at`
* `updated_at`
* `reference`

{% page-ref page="../../sorting-results.md" %}
