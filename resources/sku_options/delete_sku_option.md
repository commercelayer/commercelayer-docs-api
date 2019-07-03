---
description: How to delete an existing sku option via API
---

# Delete a sku option

To delete a sku option, send a `DELETE` request to the `/api/sku_options/:id` endpoint, where `id` is the id of the sku option that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/sku\_options/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the sku option identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/sku_options/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

