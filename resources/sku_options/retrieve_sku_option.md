---
description: How to fetch a specific sku option via API
---

# Retrieve a sku option

To fetch a single sku option, send a `GET` request to the `/api/sku_options/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/sku_options/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the sku option identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/sku_options/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

```javascript
"sku_options"
```
{% endtab %}
{% endtabs %}
