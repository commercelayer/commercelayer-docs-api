---
description: How to fetch a specific shipping zone via API
---

# Retrieve a shipping zone

To fetch a single shipping zone, send a `GET` request to the `/api/shipping_zones/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/shipping_zones/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the shipping zone identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/shipping_zones/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

```javascript
"shipping_zones"
```
{% endtab %}
{% endtabs %}
