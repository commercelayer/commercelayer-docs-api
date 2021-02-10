---
description: How to update an existing avalara account via API
---

# Update an avalara account

To update an existing avalara account, send a `PATCH` request to the `/api/avalara_accounts/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/avalara_accounts/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**name** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| attributes.**username** | `string` | Optional |
| attributes.**password** | `string` | Optional |
| attributes.**company_code** | `string` | Optional |
| attributes.**ddp** | `string` | Optional |
| relationships.**tax_categories** | `array` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the avalara account identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/avalara_accounts/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "avalara_accounts",
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

