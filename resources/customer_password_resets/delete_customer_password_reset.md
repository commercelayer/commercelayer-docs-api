---
description: How to delete an existing customer password reset via API
---

# Delete a customer password reset

To delete a customer password reset, send a `DELETE` request to the `/api/customer_password_resets/:id` endpoint, where `id` is the id of the customer password reset that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/customer_password_resets/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the customer password reset identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/customer_password_resets/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

