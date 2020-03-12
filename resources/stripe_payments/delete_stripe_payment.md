---
description: How to delete an existing stripe payment via API
---

# Delete a stripe payment

To delete a stripe payment, send a `DELETE` request to the `/api/stripe_payments/:id` endpoint, where `id` is the id of the stripe payment that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/stripe_payments/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the stripe payment identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/stripe_payments/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

