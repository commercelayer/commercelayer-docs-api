---
description: How to fetch a specific adyen gateway via API
---

# Retrieve an adyen gateway

To fetch a single adyen gateway, send a `GET` request to the `/api/adyen_gateways/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/adyen_gateways/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the adyen gateway identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/adyen_gateways/xYZkjABcde \
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
    "type": "adyen_gateways",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/adyen_gateways/xYZkjABcde"
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
      "live_url_prefix": "1797a841fbb37ca7-AdyenDemo"
    },
    "relationships": {
      "payment_methods": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/adyen_gateways/xYZkjABcde/relationships/payment_methods",
          "related": "https://yourdomain.commercelayer.io/api/adyen_gateways/xYZkjABcde/payment_methods"
        }
      },
      "adyen_payments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/adyen_gateways/xYZkjABcde/relationships/adyen_payments",
          "related": "https://yourdomain.commercelayer.io/api/adyen_gateways/xYZkjABcde/adyen_payments"
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

