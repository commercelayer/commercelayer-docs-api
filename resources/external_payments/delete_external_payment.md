---
description: How to delete an existing external payment via API
---

# Delete an external payment

To delete an external payment, send a `DELETE` request to the `/api/external_payments/:id` endpoint, where `id` is the id of the external payment that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/external\_payments/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the external payment identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/external_payments/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

