---
description: How to fetch a specific delivery lead time via API
---

# Retrieve a delivery lead time

To fetch a single delivery lead time, send a `GET` request to the `/api/delivery_lead_times/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/delivery_lead_times/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the delivery lead time identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/delivery_lead_times/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

```javascript
"delivery_lead_times"
```
{% endtab %}
{% endtabs %}
