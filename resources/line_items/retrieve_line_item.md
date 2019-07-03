---
description: How to fetch a specific line item via API
---

# Retrieve a line item

To fetch a single line item, send a `GET` request to the `/api/line_items/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/line_items/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the line item identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/line_items/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

```javascript
"line_items"
```
{% endtab %}
{% endtabs %}
