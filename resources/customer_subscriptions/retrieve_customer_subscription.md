---
description: How to fetch a specific customer subscription via API
---

# Retrieve a customer subscription

To fetch a single customer subscription, send a `GET` request to the `/api/customer_subscriptions/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/customer_subscriptions/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the customer subscription identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/customer_subscriptions/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

```javascript
"customer_subscriptions"
```
{% endtab %}
{% endtabs %}
