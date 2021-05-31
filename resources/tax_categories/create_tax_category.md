---
description: How to create a tax category via API
---

# Create a tax category

To create a new tax category, send a `POST` request to the `/api/tax_categories` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain.commercelayer.io**/api/tax\_categories**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**code** | `string` | Required |
| attributes.**sku\_code** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**sku** | `object` | Required |
| relationships.**tax\_calculator** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new tax category:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/tax_categories \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "tax_categories",
    "attributes": {
      "code": "31000"
    },
    "relationships": {
      "sku": {
        "data": {
          "type": "skus",
          "id": "QWERtyUpBa"
        }
      },
      "tax_calculator": {
        "data": {
          "type": "tax_calculators",
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
    "type": "tax_categories",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/tax_categories/xYZkjABcde"
    },
    "attributes": {
      "code": "31000",
      "sku_code": "TSHIRTMM000000FFFFFFXLXX",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "sku": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/tax_categories/xYZkjABcde/relationships/sku",
          "related": "https://yourdomain.commercelayer.io/api/tax_categories/xYZkjABcde/sku"
        }
      },
      "tax_calculator": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/tax_categories/xYZkjABcde/relationships/tax_calculator",
          "related": "https://yourdomain.commercelayer.io/api/tax_categories/xYZkjABcde/tax_calculator"
        }
      },
      "attachments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/tax_categories/xYZkjABcde/relationships/attachments",
          "related": "https://yourdomain.commercelayer.io/api/tax_categories/xYZkjABcde/attachments"
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

