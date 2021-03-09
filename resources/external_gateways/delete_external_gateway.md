---
description: How to delete an existing external gateway via API
---

# Delete an external gateway

To delete an external gateway, send a `DELETE` request to the `/api/external_gateways/:id` endpoint, where `id` is the id of the external gateway that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/external_gateways/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the external gateway identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/external_gateways/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

