---
description: How to delete an existing customer group via API
---

# Delete a customer group

To delete a customer group, send a `DELETE` request to the `/api/customer_groups/:id` endpoint, where `id` is the id of the customer group that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/customer_groups/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the customer group identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/customer_groups/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

