---
description: How to delete an existing braintree payment via API
---

# Delete a braintree payment

To delete a braintree payment, send a `DELETE` request to the `/api/braintree_payments/:id` endpoint, where `id` is the id of the braintree payment that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/braintree_payments/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the braintree payment identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/braintree_payments/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

