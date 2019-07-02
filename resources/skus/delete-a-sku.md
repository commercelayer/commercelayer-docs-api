---
description: How to delete a SKU via API
---

# Delete a SKU

To delete a SKU, send a `DELETE` request to the `/api/skus/{{id}}` endpoint, where `id` is the id of the SKU that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/skus/{{id}}**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the SKU identified by the ID "1234":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/skus/1234 \
  -H 'Authorization: Bearer your-access-token' \
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

