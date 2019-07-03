---
description: How to delete an existing customer subscription via API
---

# Delete a customer subscription

To delete a customer subscription, send a `DELETE` request to the `/api/customer_subscriptions/:id` endpoint, where `id` is the id of the customer subscription that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/customer_subscriptions/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the customer subscription identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/customer_subscriptions/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}
