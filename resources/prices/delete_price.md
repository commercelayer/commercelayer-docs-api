---
description: How to delete an existing price via API
---

# Delete a price

To delete a price, send a `DELETE` request to the `/api/prices/:id` endpoint, where `id` is the id of the price that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/prices/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the price identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/prices/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

