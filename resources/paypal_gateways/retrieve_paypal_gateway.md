---
description: How to fetch a specific paypal gateway via API
---

# Retrieve a paypal gateway

To fetch a single paypal gateway, send a `GET` request to the `/api/paypal_gateways/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/paypal_gateways/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the paypal gateway identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/paypal_gateways/xYZkjABcde \
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
    "type": "paypal_gateways",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/paypal_gateways/xYZkjABcde"
    },
    "attributes": {
      "name": "US payment gateway",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "payment_methods": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/paypal_gateways/xYZkjABcde/relationships/payment_methods",
          "related": "https://yourdomain.commercelayer.io/api/paypal_gateways/xYZkjABcde/payment_methods"
        }
      },
      "paypal_payments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/paypal_gateways/xYZkjABcde/relationships/paypal_payments",
          "related": "https://yourdomain.commercelayer.io/api/paypal_gateways/xYZkjABcde/paypal_payments"
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

