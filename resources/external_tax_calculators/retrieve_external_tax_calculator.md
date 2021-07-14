---
description: How to fetch a specific external tax calculator via API
---

# Retrieve an external tax calculator

To fetch a single external tax calculator, send a `GET` request to the `/api/external_tax_calculators/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/external_tax_calculators/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the external tax calculator identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/external_tax_calculators/xYZkjABcde \
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
      "markets": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/external_tax_calculators/xYZkjABcde/relationships/markets",
          "related": "https://yourdomain.commercelayer.io/api/external_tax_calculators/xYZkjABcde/markets"
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

