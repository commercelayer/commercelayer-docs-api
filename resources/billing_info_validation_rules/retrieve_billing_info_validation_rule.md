---
description: How to fetch a specific billing info validation rule via API
---

# Retrieve a billing info validation rule

To fetch a single billing info validation rule, send a `GET` request to the `/api/billing_info_validation_rules/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/billing\_info\_validation\_rules/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the billing info validation rule identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/billing_info_validation_rules/xYZkjABcde \
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
    "type": "billing_info_validation_rules",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/billing_info_validation_rules/xYZkjABcde"
    },
    "attributes": {
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "market": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/billing_info_validation_rules/xYZkjABcde/relationships/market",
          "related": "https://yourdomain.commercelayer.io/api/billing_info_validation_rules/xYZkjABcde/market"
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

