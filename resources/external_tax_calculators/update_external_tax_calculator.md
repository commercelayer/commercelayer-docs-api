---
description: How to update an existing external tax calculator via API
---

# Update an external tax calculator

To update an existing external tax calculator, send a `PATCH` request to the `/api/external_tax_calculators/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/external_tax_calculators/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**name** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| attributes.**tax_calculator_url** | `string` | Optional |
| relationships.**tax_categories** | `array` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the external tax calculator identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/external_tax_calculators/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "external_tax_calculators",
    "id": "xYZkjABcde",
    "attributes": {
      "reference": "ANY-EXTERNAL-REFEFERNCE"
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
    "type": "external_tax_calculators",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/external_tax_calculators/xYZkjABcde"
    },
    "attributes": {
      "name": "Personal tax calculator",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      },
      "tax_calculator_url": "https://external_calculator.yourbrand.com"
    },
    "relationships": {
      "tax_categories": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/external_tax_calculators/xYZkjABcde/relationships/tax_categories",
          "related": "https://yourdomain.commercelayer.io/api/external_tax_calculators/xYZkjABcde/tax_categories"
        }
      },
      "attachments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/external_tax_calculators/xYZkjABcde/relationships/attachments",
          "related": "https://yourdomain.commercelayer.io/api/external_tax_calculators/xYZkjABcde/attachments"
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

