---
description: How to fetch a collection of shipping zones via API
---

# List all shipping zones

To fetch a collection of shipping zones, send a `GET` request to the `/api/shipping_zones` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/shipping_zones**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of shipping zones:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/shipping_zones/ \
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
      "type": "shipping_zones",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/shipping_zones/xYZkjABcde"
      },
      "attributes": {
        "name": "Europe (main countries)"
        "country_code_regex": "AT|BE|BG|CZ|DK|EE|DE|HU|LV|LT"
        "not_country_code_regex": "AT|BE|BG|CZ|DK|EE|DE"
        "state_code_regex": "A[KLRZ]|C[AOT]|D[CE]|FL"
        "not_state_code_regex": "A[KLRZ]|C[AOT]"
        "zip_code_regex": "(?i)(JE1|JE2|JE3|JE4|JE5)"
        "not_zip_code_regex": "(?i)(JE1|JE2|JE3)"
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
      "other": "... 9 shipping zones (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/shipping_zones?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/shipping_zones?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/shipping_zones?page[number]=14&page[size]=10"
  }
}
```

{% page-ref page="../../pagination.md" %}
{% endtab %}
{% endtabs %}

### Sortable attributes

The list of shipping zones can be sorted by the following attributes:

* `name`
* `id`
* `created_at`
* `updated_at`
* `reference`

{% page-ref page="../../sorting-results.md" %}
