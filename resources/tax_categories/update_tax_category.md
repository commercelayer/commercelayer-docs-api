---
description: How to update an existing tax category via API
---

# Update a tax category

To update an existing tax category, send a `PATCH` request to the `/api/tax_categories/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/tax_categories/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**code** | `string` | Optional |
| attributes.**sku_code** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**sku** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the tax category identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/tax_categories/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "tax_categories",
    "id": "xYZkjABcde",
    "attributes": {
      "sku_code": "TSHIRTMM000000FFFFFFXLXX"
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

