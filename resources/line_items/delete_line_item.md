---
description: How to delete an existing line item via API
---

# Delete a line item

To delete a line item, send a `DELETE` request to the `/api/line_items/:id` endpoint, where `id` is the id of the line item that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/line_items/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the line item identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/line_items/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

