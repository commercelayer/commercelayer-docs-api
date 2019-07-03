---
description: How to update an existing shipping zone via API
---

# Update a shipping zone

To update an existing shipping zone, send a `PATCH` request to the `/api/shipping_zones/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/shipping_zones/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**country_code_regex** | `string` | Optional |
| attributes.**not_country_code_regex** | `string` | Optional |
| attributes.**state_code_regex** | `string` | Optional |
| attributes.**not_state_code_regex** | `string` | Optional |
| attributes.**zip_code_regex** | `string` | Optional |
| attributes.**not_zip_code_regex** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the shipping zone identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/shipping_zones/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "shipping_zones",
    "id": "xYZkjABcde",
    "attributes": {
      "name": "Europe (main countries)"
      "country_code_regex": "AT|BE|BG|CZ|DK|EE|DE|HU|LV|LT"
      "not_country_code_regex": "AT|BE|BG|CZ|DK|EE|DE"
      "state_code_regex": "A[KLRZ]|C[AOT]|D[CE]|FL"
      "not_state_code_regex": "A[KLRZ]|C[AOT]"
      "zip_code_regex": "(?i)(JE1|JE2|JE3|JE4|JE5)"
      "not_zip_code_regex": "(?i)(JE1|JE2|JE3)"
      "reference": "ANYREFEFERNCE"
      "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
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
        "reference": "ANYREFEFERNCE",
        "metadata": {
  "foo": "bar"
},
    },
    "relationships": {
      },
      "meta": {
          "mode": "test"
      }
  }
}
```
{% endtab %}
{% endtabs %}
