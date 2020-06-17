---
description: How to delete an existing refund via API
---

# Delete a refund

To delete a refund, send a `DELETE` request to the `/api/refunds/:id` endpoint, where `id` is the id of the refund that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/refunds/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the refund identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/refunds/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

