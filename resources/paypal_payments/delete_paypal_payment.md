---
description: How to delete an existing paypal payment via API
---

# Delete a paypal payment

To delete a paypal payment, send a `DELETE` request to the `/api/paypal_payments/:id` endpoint, where `id` is the id of the paypal payment that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/paypal_payments/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the paypal payment identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/paypal_payments/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}
