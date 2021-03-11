---
description: How to fetch a specific tax rule via API
---

# Retrieve a tax rule

To fetch a single tax rule, send a `GET` request to the `/api/tax_rules/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/tax_rules/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the tax rule identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/tax_rules/xYZkjABcde \
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
    "type": "tax_rules",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/tax_rules/xYZkjABcde"
    },
    "attributes": {
      "name": "Fixed 22%",
      "tax_rate": 0.22,
      "country_code_regex": "AT|BE|BG|CZ|DK|EE|DE|HU|LV|LT",
      "not_country_code_regex": "AT|BE|BG|CZ|DK|EE|DE",
      "state_code_regex": "A[KLRZ]|C[AOT]|D[CE]|FL",
      "not_state_code_regex": "A[KLRZ]|C[AOT]",
      "zip_code_regex": "(?i)(JE1|JE2|JE3|JE4|JE5)",
      "not_zip_code_regex": "(?i)(JE1|JE2|JE3)",
      "freight_taxable": false,
      "payment_method_taxable": false,
      "gift_card_taxable": false,
      "adjustment_taxable": false,
      "breakdown": {
        "41": {
          "tax_rate": 0.22
        }
      },
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "manual_tax_calculator": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/tax_rules/xYZkjABcde/relationships/manual_tax_calculator",
          "related": "https://yourdomain.commercelayer.io/api/tax_rules/xYZkjABcde/manual_tax_calculator"
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

