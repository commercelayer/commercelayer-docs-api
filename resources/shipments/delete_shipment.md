---
description: How to delete an existing shipment via API
---

# Delete a shipment

To delete a shipment, send a `DELETE` request to the `/api/shipments/:id` endpoint, where `id` is the id of the shipment that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/shipments/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the shipment identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

