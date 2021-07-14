---
description: How to fetch a specific carrier account via API
---

# Retrieve a carrier account

To fetch a single carrier account, send a `GET` request to the `/api/carrier_accounts/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/carrier_accounts/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the carrier account identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/carrier_accounts/xYZkjABcde \
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
    "type": "carrier_accounts",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/carrier_accounts/xYZkjABcde"
    },
    "attributes": {
      "name": "UPS",
      "easypost_type": "UPS",
      "easypost_id": "xxxx-yyyy-zzzz",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "market": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/carrier_accounts/xYZkjABcde/relationships/market",
          "related": "https://yourdomain.commercelayer.io/api/carrier_accounts/xYZkjABcde/market"
        }
      },
      "attachments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/carrier_accounts/xYZkjABcde/relationships/attachments",
          "related": "https://yourdomain.commercelayer.io/api/carrier_accounts/xYZkjABcde/attachments"
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

