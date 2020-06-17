---
description: How to delete an existing authorization via API
---

# Delete an authorization

To delete an authorization, send a `DELETE` request to the `/api/authorizations/:id` endpoint, where `id` is the id of the authorization that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/authorizations/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the authorization identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/authorizations/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

