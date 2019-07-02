---
description: How to create An address via API
---

# Create An address

To create a new address, send a `POST` request to the `/api/addresses` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

```text
**POST** https://yourdomain.commercelayer.io**/api/addresses**
```

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**business** | `boolean` | optional, default is 'false' |
| attributes.**first_name** | `string` | required if 'business' is 'false' |
| attributes.**last_name** | `string` | required if 'business' is 'false' |
| attributes.**company** | `string` | required if 'business' is 'true' |
| attributes.**full_name** | `string` |  |
| attributes.**line_1** | `string` | required |
| attributes.**line_2** | `string` | optional |
| attributes.**city** | `string` | required |
| attributes.**zip_code** | `string` | required |
| attributes.**state_code** | `string` | required |
| attributes.**country_code** | `string` | required |
| attributes.**phone** | `string` | required |
| attributes.**full_address** | `string` |  |
| attributes.**name** | `string` |  |
| attributes.**email** | `string` | optional |
| attributes.**notes** | `string` | optional |
| attributes.**lat** | `float` | optional |
| attributes.**lng** | `float` | optional |
| attributes.**is_localized** | `boolean` | optional |
| attributes.**is_geocoded** | `boolean` | optional |
| attributes.**provider_name** | `string` | optional |
| attributes.**map_url** | `string` | optional |
| attributes.**static_map_url** | `string` | optional |
| attributes.**billing_info** | `string` | configurable |
| attributes.**id** | `string` | required |
| attributes.**created_at** | `datetime` | required |
| attributes.**updated_at** | `datetime` | required |
| attributes.**reference** | `string` | optional |
| attributes.**metadata** | `object` | optional |
| relationships.**geocoder** | `has_one` | optional |

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
      "line_1": "2883 Geraldine Lane"
      "city": "New York"
      "zip_code": "10013"
      "state_code": "NY"
      "country_code": "US"
      "phone": "(212) 646-338-1228"
    },
    "relationships": {
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `address` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "addresses",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/addresses/xYZkjABcde"
    },
    "attributes": {
        "business": "false"
        "first_name": "John"
        "last_name": "Smith"
        "company": "The Red Brand Inc."
        "full_name": "John Smith"
        "line_1": "2883 Geraldine Lane"
        "line_2": "Apt.23"
        "city": "New York"
        "zip_code": "10013"
        "state_code": "NY"
        "country_code": "US"
        "phone": "(212) 646-338-1228"
        "full_address": "2883 Geraldine Lane Apt.23, 10013 New York NY (US) (212) 646-338-1228"
        "name": "John Smith, 2883 Geraldine Lane Apt.23, 10013 New York NY (US) (212) 646-338-1228"
        "email": "john@example.com"
        "notes": "Please ring the bell twice"
        "lat": "40.6971494"
        "lng": "-74.2598672"
        "is_localized": "true"
        "is_geocoded": "true"
        "provider_name": "google"
        "map_url": "https://www.google.com/maps/search/?api=1&query=40.6971494,-74.2598672"
        "static_map_url": "https://maps.googleapis.com/maps/api/staticmap?center=40.6971494,-74.2598672&size=640x320&zoom=15"
        "billing_info": "VAT ID IT02382940977"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
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
