---
description: How to fetch a specific avalara account via API
---

# Retrieve an avalara account

To fetch a single avalara account, send a `GET` request to the `/api/avalara_accounts/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/avalara_accounts/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the avalara account identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/avalara_accounts/xYZkjABcde \
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
    "type": "avalara_accounts",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/avalara_accounts/xYZkjABcde"
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
      "username": "user@mydomain.com",
      "company_code": "MYCOMPANY",
      "ddp": "true"
    },
    "relationships": {
      "tax_categories": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/avalara_accounts/xYZkjABcde/relationships/tax_categories",
          "related": "https://yourdomain.commercelayer.io/api/avalara_accounts/xYZkjABcde/tax_categories"
        }
      },
      "markets": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/avalara_accounts/xYZkjABcde/relationships/markets",
          "related": "https://yourdomain.commercelayer.io/api/avalara_accounts/xYZkjABcde/markets"
        }
      },
      "attachments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/avalara_accounts/xYZkjABcde/relationships/attachments",
          "related": "https://yourdomain.commercelayer.io/api/avalara_accounts/xYZkjABcde/attachments"
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

