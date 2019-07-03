---
description: How to delete an existing delivery lead time via API
---

# Delete a delivery lead time

To delete a delivery lead time, send a `DELETE` request to the `/api/delivery_lead_times/:id` endpoint, where `id` is the id of the delivery lead time that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/delivery_lead_times/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the delivery lead time identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/delivery_lead_times/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}
