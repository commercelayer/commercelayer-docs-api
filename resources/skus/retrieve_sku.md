---
description: How to fetch a specific SKU via API
---

# Retrieve an SKU

To fetch a single SKU, send a `GET` request to the `/api/skus/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/skus/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the SKU identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/skus/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

```javascript
"skus"
```
{% endtab %}
{% endtabs %}
