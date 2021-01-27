---
description: How to fetch a specific shipping zone via API
---

# Retrieve a shipping zone

To fetch a single shipping zone, send a `GET` request to the `/api/shipping_zones/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/shipping_zones/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the shipping zone identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/shipping_zones/xYZkjABcde \
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
    "type": "shipping_zones",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/shipping_zones/xYZkjABcde"
    },
    "attributes": {
      "name": "Europe (main countries)",
      "country_code_regex": "AT|BE|BG|CZ|DK|EE|DE|HU|LV|LT",
      "not_country_code_regex": "AT|BE|BG|CZ|DK|EE|DE",
      "state_code_regex": "A[KLRZ]|C[AOT]|D[CE]|FL",
      "not_state_code_regex": "A[KLRZ]|C[AOT]",
      "zip_code_regex": "(?i)(JE1|JE2|JE3|JE4|JE5)",
      "not_zip_code_regex": "(?i)(JE1|JE2|JE3)",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "attachments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipping_zones/xYZkjABcde/relationships/attachments",
          "related": "https://yourdomain.commercelayer.io/api/shipping_zones/xYZkjABcde/attachments"
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

