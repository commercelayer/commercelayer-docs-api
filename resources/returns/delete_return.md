---
description: How to delete an existing return via API
---

# Delete a return

To delete a return, send a `DELETE` request to the `/api/returns/:id` endpoint, where `id` is the id of the return that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/returns/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the return identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/returns/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

