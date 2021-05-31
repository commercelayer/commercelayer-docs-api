---
description: How to delete an existing checkout com payment via API
---

# Delete a checkout com payment

To delete a checkout com payment, send a `DELETE` request to the `/api/checkout_com_payments/:id` endpoint, where `id` is the id of the checkout com payment that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/checkout\_com\_payments/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the checkout com payment identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/checkout_com_payments/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

