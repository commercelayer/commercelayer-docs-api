---
description: How to delete an existing external promotion via API
---

# Delete an external promotion

To delete an external promotion, send a `DELETE` request to the `/api/external_promotions/:id` endpoint, where `id` is the id of the external promotion that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/external\_promotions/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the external promotion identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/external_promotions/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

