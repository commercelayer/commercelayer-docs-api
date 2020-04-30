---
description: How to delete an existing SKU list via API
---

# Delete a SKU list

To delete a SKU list, send a `DELETE` request to the `/api/sku_lists/:id` endpoint, where `id` is the id of the SKU list that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/sku_lists/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the SKU list identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/sku_lists/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

