---
description: How to delete an existing free shipping promotion via API
---

# Delete a free shipping promotion

To delete a free shipping promotion, send a `DELETE` request to the `/api/free_shipping_promotions/:id` endpoint, where `id` is the id of the free shipping promotion that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/free\_shipping\_promotions/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the free shipping promotion identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/free_shipping_promotions/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

