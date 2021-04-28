---
description: How to delete an existing manual tax calculator via API
---

# Delete a manual tax calculator

To delete a manual tax calculator, send a `DELETE` request to the `/api/manual_tax_calculators/:id` endpoint, where `id` is the id of the manual tax calculator that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/manual_tax_calculators/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the manual tax calculator identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/manual_tax_calculators/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

