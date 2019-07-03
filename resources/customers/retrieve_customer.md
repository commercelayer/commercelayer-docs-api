---
description: How to fetch a specific customer via API
---

# Retrieve a customer

To fetch a single customer, send a `GET` request to the `/api/customers/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/customers/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the customer identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/customers/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

```javascript
"customers"
```
{% endtab %}
{% endtabs %}
