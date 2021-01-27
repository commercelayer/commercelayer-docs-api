---
description: How to delete an existing shipping method via API
---

# Delete a shipping method

To delete a shipping method, send a `DELETE` request to the `/api/shipping_methods/:id` endpoint, where `id` is the id of the shipping method that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/shipping\_methods/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the shipping method identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

