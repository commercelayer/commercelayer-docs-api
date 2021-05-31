---
description: How to delete an existing braintree gateway via API
---

# Delete a braintree gateway

To delete a braintree gateway, send a `DELETE` request to the `/api/braintree_gateways/:id` endpoint, where `id` is the id of the braintree gateway that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/braintree\_gateways/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the braintree gateway identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/braintree_gateways/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

