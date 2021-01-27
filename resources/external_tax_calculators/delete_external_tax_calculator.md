---
description: How to delete an existing external tax calculator via API
---

# Delete an external tax calculator

To delete an external tax calculator, send a `DELETE` request to the `/api/external_tax_calculators/:id` endpoint, where `id` is the id of the external tax calculator that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/external\_tax\_calculators/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the external tax calculator identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/external_tax_calculators/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

