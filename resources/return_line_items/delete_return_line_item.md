---
description: How to delete an existing return line item via API
---

# Delete a return line item

To delete a return line item, send a `DELETE` request to the `/api/return_line_items/:id` endpoint, where `id` is the id of the return line item that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/return_line_items/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the return line item identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/return_line_items/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

