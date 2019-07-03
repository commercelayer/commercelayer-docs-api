---
description: How to fetch a specific order via API
---

# Retrieve an order

To fetch a single order, send a `GET` request to the `/api/orders/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/orders/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the order identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/orders/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

```javascript
"orders"
```
{% endtab %}
{% endtabs %}
