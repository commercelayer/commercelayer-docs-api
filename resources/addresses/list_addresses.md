---
description: How to fetch a collection of addresses via API
---

# List all addresses

To fetch a collection of addresses, send a `GET` request to the `/api/addresses` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/addresses**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of addresses:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/addresses/ \
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
      "business": "false",
      "first_name": "John",
      "last_name": "Smith",
      "company": "The Red Brand Inc.",
      "full_name": "John Smith",
      "line_1": "2883 Geraldine Lane",
      "line_2": "Apt.23",
      "city": "New York",
      "zip_code": "10013",
      "state_code": "NY",
      "country_code": "US",
      "phone": "(212) 646-338-1228",
      "full_address": "2883 Geraldine Lane Apt.23, 10013 New York NY (US) (212) 646-338-1228",
      "name": "John Smith, 2883 Geraldine Lane Apt.23, 10013 New York NY (US) (212) 646-338-1228",
      "email": "john@example.com",
      "notes": "Please ring the bell twice",
      "lat": "40.6971494",
      "lng": "-74.2598672",
      "is_localized": "true",
      "is_geocoded": "true",
      "provider_name": "google",
      "map_url": "https://www.google.com/maps/search/?api=1&query=40.6971494,-74.2598672",
      "static_map_url": "https://maps.googleapis.com/maps/api/staticmap?center=40.6971494,-74.2598672&size=640x320&zoom=15",
      "billing_info": "VAT ID IT02382940977",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    {
      "other": "... 9 addresses (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/addresses?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/addresses?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/addresses?page[number]=14&page[size]=10"
  }
}


{
  "data": [
    {
      "id": "xYZkjABcde",
      "type": "addresses",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/addresses/xYZkjABcde"
      },
      "attributes": {
        "business": "false",
        "first_name": "John",
        "last_name": "Smith",
        "company": "The Red Brand Inc.",
        "full_name": "John Smith",
        "line_1": "2883 Geraldine Lane",
        "line_2": "Apt.23",
        "city": "New York",
        "zip_code": "10013",
        "state_code": "NY",
        "country_code": "US",
        "phone": "(212) 646-338-1228",
        "full_address": "2883 Geraldine Lane Apt.23, 10013 New York NY (US) (212) 646-338-1228",
        "name": "John Smith, 2883 Geraldine Lane Apt.23, 10013 New York NY (US) (212) 646-338-1228",
        "email": "john@example.com",
        "notes": "Please ring the bell twice",
        "lat": "40.6971494",
        "lng": "-74.2598672",
        "is_localized": "true",
        "is_geocoded": "true",
        "provider_name": "google",
        "map_url": "https://www.google.com/maps/search/?api=1&query=40.6971494,-74.2598672",
        "static_map_url": "https://maps.googleapis.com/maps/api/staticmap?center=40.6971494,-74.2598672&size=640x320&zoom=15",
        "billing_info": "VAT ID IT02382940977",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANYREFEFERNCE",
        "metadata": {
  "foo": "bar"
},
      },
      "relationships": {
        "geocoder": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/addresses/xYZkjABcde/relationships/geocoder",
              "related": "https://yourdomain.commercelayer.io/api/addresses/xYZkjABcde/geocoder"
          }
        },
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 addresses (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/addresses?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/addresses?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/addresses?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of addresses can be sorted by the following attributes:

* `city`
* `country_code`
* `id`
* `created_at`
* `updated_at`
* `reference`

{% page-ref page="../../sorting-results.md" %}

