---
description: How to create a tax rule via API
---

# Create a tax rule

To create a new tax rule, send a `POST` request to the `/api/tax_rules` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain.commercelayer.io**/api/tax\_rules**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**tax\_rate** | `float` | Optional |
| attributes.**country\_code\_regex** | `string` | Optional |
| attributes.**not\_country\_code\_regex** | `string` | Optional |
| attributes.**state\_code\_regex** | `string` | Optional |
| attributes.**not\_state\_code\_regex** | `string` | Optional |
| attributes.**zip\_code\_regex** | `string` | Optional |
| attributes.**not\_zip\_code\_regex** | `string` | Optional |
| attributes.**freight\_taxable** | `boolean` | Optional, default is 'false' |
| attributes.**payment\_method\_taxable** | `boolean` | Optional, default is 'false' |
| attributes.**gift\_card\_taxable** | `boolean` | Optional, default is 'false' |
| attributes.**adjustment\_taxable** | `boolean` | Optional, default is 'false' |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**manual\_tax\_calculator** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new tax rule:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/tax_rules \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "tax_rules",
    "attributes": {
      "name": "Fixed 22%"
    },
    "relationships": {
      "manual_tax_calculator": {
        "data": {
          "type": "manual_tax_calculators",
          "id": "QWERtyUpBa"
        }
      }
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

