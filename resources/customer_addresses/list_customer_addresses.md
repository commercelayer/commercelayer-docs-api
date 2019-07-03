---
description: How to fetch a list of customer addresses via API
---

# List all customer addresses

To fetch a collection of customer addresses, send a `GET` request to the `/api/customer_addresses` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/customer\_addresses**

### **Example**

The following request fetches a collection of customer addresses:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/customer_addresses/ \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```

On success, the API responds with a `200 OK` status code, returning a paginated collection of resource objects:

```javascript
{
  "data": [
    {
      "id": "xYZkjABcde",
      "type": "customer_addresses",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/customer_addresses/xYZkjABcde"
      },
      "attributes": {
        "name": "John Smith, 2883 Geraldine Lane Apt.23, 10013 New York NY (US) (212) 646-338-1228"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
      },
      "relationships": {
        "customer": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/customer_addresses/xYZkjABcde/relationships/customer",
              "related": "https://yourdomain.commercelayer.io/api/customer_addresses/xYZkjABcde/customer"
          }
        }
        "address": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/customer_addresses/xYZkjABcde/relationships/address",
              "related": "https://yourdomain.commercelayer.io/api/customer_addresses/xYZkjABcde/address"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 customer addresses (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/customer_addresses?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/customer_addresses?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/customer_addresses?page[number]=14&page[size]=10"
  }
}
```

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of customer addresses can be sorted by the following attributes:

* `id`
* `created_at`
* `updated_at`
* `reference`

{% page-ref page="../../sorting-results.md" %}

