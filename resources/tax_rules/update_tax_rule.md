---
description: How to update an existing tax rule via API
---

# Update a tax rule

To update an existing tax rule, send a `PATCH` request to the `/api/tax_rules/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://yourdomain.commercelayer.io**/api/tax\_rules/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**name** | `string` | Optional |
| attributes.**tax\_rate** | `float` | Optional |
| attributes.**country\_code\_regex** | `string` | Optional |
| attributes.**not\_country\_code\_regex** | `string` | Optional |
| attributes.**state\_code\_regex** | `string` | Optional |
| attributes.**not\_state\_code\_regex** | `string` | Optional |
| attributes.**zip\_code\_regex** | `string` | Optional |
| attributes.**not\_zip\_code\_regex** | `string` | Optional |
| attributes.**freight\_taxable** | `boolean` | Optional |
| attributes.**payment\_method\_taxable** | `boolean` | Optional |
| attributes.**gift\_card\_taxable** | `boolean` | Optional |
| attributes.**adjustment\_taxable** | `boolean` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**manual\_tax\_calculator** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the tax rule identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/tax_rules/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "tax_rules",
    "id": "xYZkjABcde",
    "attributes": {
      "country_code_regex": "AT|BE|BG|CZ|DK|EE|DE|HU|LV|LT"
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
    "type": "tax_rules",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/tax_rules/xYZkjABcde"
    },
    "attributes": {
      "name": "Fixed 22%",
      "tax_rate": "0.22",
      "country_code_regex": "AT|BE|BG|CZ|DK|EE|DE|HU|LV|LT",
      "not_country_code_regex": "AT|BE|BG|CZ|DK|EE|DE",
      "state_code_regex": "A[KLRZ]|C[AOT]|D[CE]|FL",
      "not_state_code_regex": "A[KLRZ]|C[AOT]",
      "zip_code_regex": "(?i)(JE1|JE2|JE3|JE4|JE5)",
      "not_zip_code_regex": "(?i)(JE1|JE2|JE3)",
      "freight_taxable": "false",
      "payment_method_taxable": "false",
      "gift_card_taxable": "false",
      "adjustment_taxable": "false",
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

