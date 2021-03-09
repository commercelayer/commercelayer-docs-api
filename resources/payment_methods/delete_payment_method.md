---
description: How to delete an existing payment method via API
---

# Delete a payment method

To delete a payment method, send a `DELETE` request to the `/api/payment_methods/:id` endpoint, where `id` is the id of the payment method that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/payment_methods/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the payment method identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/payment_methods/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

