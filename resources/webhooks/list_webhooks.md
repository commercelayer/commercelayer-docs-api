---
description: How to fetch a list of webhooks via API
---

# List all webhooks

To fetch a collection of webhooks, send a `GET` request to the `/api/webhooks` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/webhooks**

### **Example**

The following request fetches a collection of webhooks:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/webhooks/ \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```

On success, the API responds with a `200 OK` status code, returning a paginated collection of resource objects:

```javascript
{
  "data": [
    {
      "id": "xYZkjABcde",
      "type": "webhooks",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/webhooks/xYZkjABcde"
      },
      "attributes": {
        "topic": "orders.place"
        "callback_url": "https://yourapp.com/webhooks"
        "include_resources": "[customer, shipping_address, billing_address]"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
      },
      "relationships": {
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 webhooks (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/webhooks?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/webhooks?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/webhooks?page[number]=14&page[size]=10"
  }
}
```

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of webhooks can be sorted by the following attributes:

* `id`
* `created_at`
* `updated_at`
* `reference`

{% page-ref page="../../sorting-results.md" %}

