---
description: How to delete an existing bundle via API
---

# Delete a bundle

To delete a bundle, send a `DELETE` request to the `/api/bundles/:id` endpoint, where `id` is the id of the bundle that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/bundles/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the bundle identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/bundles/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

