---
description: How to fetch a specific checkout com gateway via API
---

# Retrieve a checkout com gateway

To fetch a single checkout com gateway, send a `GET` request to the `/api/checkout_com_gateways/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/checkout_com_gateways/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the checkout com gateway identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde \
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
    "type": "checkout_com_gateways",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde"
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
      "webhook_endpoint_id": "xxxx-yyyy-zzzz",
      "webhook_endpoint_secret": "xxxx-yyyy-zzzz",
      "webhook_endpoint_url": "https://core.commercelayer.co/webhook_callbacks/checkout_com_gateways/xxxxx"
    },
    "relationships": {
      "payment_methods": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde/relationships/payment_methods",
          "related": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde/payment_methods"
        }
      },
      "checkout_com_payments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde/relationships/checkout_com_payments",
          "related": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde/checkout_com_payments"
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

