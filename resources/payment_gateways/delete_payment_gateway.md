---
description: How to delete an existing payment gateway via API
---

# Delete a payment gateway

To delete a payment gateway, send a `DELETE` request to the `/api/payment_gateways/:id` endpoint, where `id` is the id of the payment gateway that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/payment_gateways/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the payment gateway identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/payment_gateways/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

