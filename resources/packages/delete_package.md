---
description: How to delete an existing package via API
---

# Delete a package

To delete a package, send a `DELETE` request to the `/api/packages/:id` endpoint, where `id` is the id of the package that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/packages/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the package identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/packages/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

