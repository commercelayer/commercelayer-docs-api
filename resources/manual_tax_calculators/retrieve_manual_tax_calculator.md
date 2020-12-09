---
description: How to fetch a specific manual tax calculator via API
---

# Retrieve a manual tax calculator

To fetch a single manual tax calculator, send a `GET` request to the `/api/manual_tax_calculators/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/manual_tax_calculators/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the manual tax calculator identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/manual_tax_calculators/xYZkjABcde \
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
    "type": "manual_tax_calculators",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/manual_tax_calculators/xYZkjABcde"
    },
    "attributes": {
      "name": "Personal tax calculator",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "tax_categories": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/manual_tax_calculators/xYZkjABcde/relationships/tax_categories",
          "related": "https://yourdomain.commercelayer.io/api/manual_tax_calculators/xYZkjABcde/tax_categories"
        }
      },
      "tax_rules": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/manual_tax_calculators/xYZkjABcde/relationships/tax_rules",
          "related": "https://yourdomain.commercelayer.io/api/manual_tax_calculators/xYZkjABcde/tax_rules"
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

