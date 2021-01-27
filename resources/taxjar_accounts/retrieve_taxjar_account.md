---
description: How to fetch a specific taxjar account via API
---

# Retrieve a taxjar account

To fetch a single taxjar account, send a `GET` request to the `/api/taxjar_accounts/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/taxjar\_accounts/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the taxjar account identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/taxjar_accounts/xYZkjABcde \
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
    "type": "taxjar_accounts",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/taxjar_accounts/xYZkjABcde"
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
          "self": "https://yourdomain.commercelayer.io/api/taxjar_accounts/xYZkjABcde/relationships/tax_categories",
          "related": "https://yourdomain.commercelayer.io/api/taxjar_accounts/xYZkjABcde/tax_categories"
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

