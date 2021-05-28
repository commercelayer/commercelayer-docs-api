---
description: How to fetch a specific external gateway via API
---

# Retrieve an external gateway

To fetch a single external gateway, send a `GET` request to the `/api/external_gateways/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/external\_gateways/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the external gateway identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/external_gateways/xYZkjABcde \
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
    "type": "external_gateways",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/external_gateways/xYZkjABcde"
    },
    "attributes": {
      "name": "US payment gateway",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      },
      "shared_secret": "xxxx-yyyy-zzzz",
      "authorize_url": "https://external_gateway.com/authorize",
      "capture_url": "https://external_gateway.com/capture",
      "void_url": "https://external_gateway.com/void",
      "refund_url": "https://external_gateway.com/refund"
    },
    "relationships": {
      "payment_methods": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/external_gateways/xYZkjABcde/relationships/payment_methods",
          "related": "https://yourdomain.commercelayer.io/api/external_gateways/xYZkjABcde/payment_methods"
        }
      },
      "external_payments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/external_gateways/xYZkjABcde/relationships/external_payments",
          "related": "https://yourdomain.commercelayer.io/api/external_gateways/xYZkjABcde/external_payments"
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

