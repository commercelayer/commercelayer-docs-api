---
description: How to delete an existing void via API
---

# Delete a void

To delete a void, send a `DELETE` request to the `/api/voids/:id` endpoint, where `id` is the id of the void that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/voids/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the void identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/voids/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

