---
description: How to delete an existing capture via API
---

# Delete a capture

To delete a capture, send a `DELETE` request to the `/api/captures/:id` endpoint, where `id` is the id of the capture that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/captures/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the capture identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/captures/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

