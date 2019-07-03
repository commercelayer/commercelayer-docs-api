---
description: How to fetch a specific shipping method via API
---

# Retrieve a shipping method

To fetch a single shipping method, send a `GET` request to the `/api/shipping_methods/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/shipping_methods/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the shipping method identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

```javascript
"shipping_methods"
```
{% endtab %}
{% endtabs %}
