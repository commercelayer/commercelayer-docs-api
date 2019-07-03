---
description: How to delete an existing order via API
---

# Delete an order

To delete an order, send a `DELETE` request to the `/api/orders/:id` endpoint, where `id` is the id of the order that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/orders/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the order identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/orders/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}
