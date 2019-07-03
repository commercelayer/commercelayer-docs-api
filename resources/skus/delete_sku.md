---
description: How to delete an existing SKU via API
---

# Delete an SKU

To delete an SKU, send a `DELETE` request to the `/api/skus/:id` endpoint, where `id` is the id of the SKU that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/skus/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the SKU identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/skus/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}
