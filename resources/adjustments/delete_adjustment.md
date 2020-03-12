---
description: How to delete an existing adjustment via API
---

# Delete an adjustment

To delete an adjustment, send a `DELETE` request to the `/api/adjustments/:id` endpoint, where `id` is the id of the adjustment that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/adjustments/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the adjustment identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/adjustments/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

