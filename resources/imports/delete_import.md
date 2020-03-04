---
description: How to delete an existing import via API
---

# Delete an import

To delete an import, send a `DELETE` request to the `/api/imports/:id` endpoint, where `id` is the id of the import that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/imports/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the import identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/imports/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

