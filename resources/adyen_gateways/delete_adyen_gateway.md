---
description: How to delete an existing adyen gateway via API
---

# Delete an adyen gateway

To delete an adyen gateway, send a `DELETE` request to the `/api/adyen_gateways/:id` endpoint, where `id` is the id of the adyen gateway that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/adyen\_gateways/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the adyen gateway identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/adyen_gateways/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

