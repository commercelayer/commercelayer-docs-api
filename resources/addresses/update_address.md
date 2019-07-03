---
description: How to update an existing address via API
---

# Update an address

To update an existing address, send a `PATCH` request to the `/api/addresses/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://yourdomain.commercelayer.io**/api/addresses/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**business** | `boolean` | Optional, default is 'false' |
| attributes.**first\_name** | `string` | Required if 'business' is 'false' |
| attributes.**last\_name** | `string` | Required if 'business' is 'false' |
| attributes.**company** | `string` | Required if 'business' is 'true' |
| attributes.**line\_1** | `string` | Required |
| attributes.**line\_2** | `string` | Optional |
| attributes.**city** | `string` | Required |
| attributes.**zip\_code** | `string` | Required |
| attributes.**state\_code** | `string` | Required |
| attributes.**country\_code** | `string` | Required |
| attributes.**phone** | `string` | Required |
| attributes.**email** | `string` | Optional |
| attributes.**notes** | `string` | Optional |
| attributes.**lat** | `float` | Optional |
| attributes.**lng** | `float` | Optional |
| attributes.**billing\_info** | `string` | Configurable |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**geocoder** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the address identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/addresses/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "addresses",
    "id": "xYZkjABcde",
    "attributes": {
      "business": "false"
    },
    "relationships": {
      "geocoder": {
        "data": {
          "type": "geocoders",
          "id": "QWERtyUpBa"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning the updated resource object:

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
      "reference": "ANYREFEFERNCE",
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

