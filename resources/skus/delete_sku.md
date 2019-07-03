---
description: How to delete an existing sku via API
---

# Delete a SKU

To delete a sku, send a `DELETE` request to the `/api/skus/:id` endpoint, where `id` is the id of the sku that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/skus/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the sku identified by the ID "xYZkjABcde":

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

