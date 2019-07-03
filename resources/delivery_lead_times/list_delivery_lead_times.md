---
description: How to fetch a list of delivery lead times via API
---

# List all delivery lead times

To fetch a collection of delivery lead times, send a `GET` request to the `/api/delivery_lead_times` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/delivery\_lead\_times**

### **Example**

The following request fetches a collection of delivery lead times:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/delivery_lead_times/ \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```

On success, the API responds with a `200 OK` status code, returning a paginated collection of resource objects:

```javascript
{
  "data": [
    {
      "id": "xYZkjABcde",
      "type": "delivery_lead_times",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/delivery_lead_times/xYZkjABcde"
      },
      "attributes": {
        "min_hours": "48"
        "max_hours": "72"
        "min_days": "2"
        "max_days": "3"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
      },
      "relationships": {
        "stock_location": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/delivery_lead_times/xYZkjABcde/relationships/stock_location",
              "related": "https://yourdomain.commercelayer.io/api/delivery_lead_times/xYZkjABcde/stock_location"
          }
        }
        "shipping_method": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/delivery_lead_times/xYZkjABcde/relationships/shipping_method",
              "related": "https://yourdomain.commercelayer.io/api/delivery_lead_times/xYZkjABcde/shipping_method"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 delivery lead times (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/delivery_lead_times?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/delivery_lead_times?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/delivery_lead_times?page[number]=14&page[size]=10"
  }
}
```

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of delivery lead times can be sorted by the following attributes:

* `min_hours`
* `max_hours`
* `id`
* `created_at`
* `updated_at`
* `reference`

{% page-ref page="../../sorting-results.md" %}

