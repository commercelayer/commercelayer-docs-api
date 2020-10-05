---
description: How to delete an existing address via API
---

# Delete an address

To delete an address, send a `DELETE` request to the `/api/addresses/:id` endpoint, where `id` is the id of the address that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/addresses/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the address identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/addresses/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

