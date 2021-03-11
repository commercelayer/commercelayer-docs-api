---
description: How to fetch a collection of tax rules via API
---

# List all tax rules

To fetch a collection of tax rules, send a `GET` request to the `/api/tax_rules` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/tax_rules**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of tax rules:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/tax_rules/ \
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
    },
    {
      "other": "... 9 tax_rules (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/tax_rules?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/tax_rules?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/tax_rules?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of tax rules can be sorted by the following attributes:

* `name`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

