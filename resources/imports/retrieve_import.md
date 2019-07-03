---
description: How to fetch a specific import via API
---

# Retrieve an import

To fetch a single import, send a `GET` request to the `/api/imports/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/imports/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the import identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/imports/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

```javascript
"imports"
```
{% endtab %}
{% endtabs %}
