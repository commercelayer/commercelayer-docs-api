---
description: How to fetch a specific credit card via API
---

# Retrieve a credit card

To fetch a single credit card, send a `GET` request to the `/api/credit_cards/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/credit_cards/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the credit card identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/credit_cards/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

```javascript
"credit_cards"
```
{% endtab %}
{% endtabs %}
