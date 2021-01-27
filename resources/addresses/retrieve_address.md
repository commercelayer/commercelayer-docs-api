---
description: How to fetch a specific address via API
---

# Retrieve an address

To fetch a single address, send a `GET` request to the `/api/addresses/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/addresses/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the address identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/addresses/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

```javascript
{
  "data": {
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
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "geocoder": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/addresses/xYZkjABcde/relationships/geocoder",
          "related": "https://yourdomain.commercelayer.io/api/addresses/xYZkjABcde/geocoder"
        }
      }
    },
    "meta": {
      "mode": "test"
    }
  }
}
```
{% endtab %}
{% endtabs %}

