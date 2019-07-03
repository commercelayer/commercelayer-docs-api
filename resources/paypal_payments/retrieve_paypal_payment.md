---
description: How to fetch a specific paypal payment via API
---

# Retrieve a paypal payment

To fetch a single paypal payment, send a `GET` request to the `/api/paypal_payments/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/paypal_payments/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the paypal payment identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/paypal_payments/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

```javascript
"paypal_payments"
```
{% endtab %}
{% endtabs %}
