---
description: How to delete an existing inventory return location via API
---

# Delete an inventory return location

To delete an inventory return location, send a `DELETE` request to the `/api/inventory_return_locations/:id` endpoint, where `id` is the id of the inventory return location that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/inventory\_return\_locations/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the inventory return location identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/inventory_return_locations/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

