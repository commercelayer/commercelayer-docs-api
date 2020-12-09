---
description: How to fetch a specific tax category via API
---

# Retrieve a tax category

To fetch a single tax category, send a `GET` request to the `/api/tax_categories/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/tax_categories/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the tax category identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/tax_categories/xYZkjABcde \
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

