---
description: How to create an address via API
---

# Create an address

To create a new address, send a `POST` request to the `/api/addresses` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/addresses**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**business** | `boolean` | Optional, default is 'false' |
| attributes.**first_name** | `string` | Required if 'business' is 'false' |
| attributes.**last_name** | `string` | Required if 'business' is 'false' |
| attributes.**company** | `string` | Required if 'business' is 'true' |
| attributes.**line_1** | `string` | Required |
| attributes.**line_2** | `string` | Optional |
| attributes.**city** | `string` | Required |
| attributes.**zip_code** | `string` | Required |
| attributes.**state_code** | `string` | Required |
| attributes.**country_code** | `string` | Required |
| attributes.**phone** | `string` | Required |
| attributes.**email** | `string` | Optional |
| attributes.**notes** | `string` | Optional |
| attributes.**lat** | `float` | Optional |
| attributes.**lng** | `float` | Optional |
| attributes.**billing_info** | `string` | Configurable |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**geocoder** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new address:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/addresses \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "addresses",
    "attributes": {
      "line_1": "2883 Geraldine Lane",
      "city": "New York",
      "zip_code": "10013",
      "state_code": "NY",
      "country_code": "US",
      "phone": "(212) 646-338-1228"
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created resource object:

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
