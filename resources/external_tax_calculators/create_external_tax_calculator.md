---
description: How to create an external tax calculator via API
---

# Create an external tax calculator

To create a new external tax calculator, send a `POST` request to the `/api/external_tax_calculators` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain.commercelayer.io**/api/external\_tax\_calculators**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| attributes.**tax\_calculator\_url** | `string` | Required |
| relationships.**tax\_categories** | `array` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new external tax calculator:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/external_tax_calculators \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "external_tax_calculators",
    "attributes": {
      "name": "Personal tax calculator",
      "tax_calculator_url": "https://external_calculator.yourbrand.com"
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

