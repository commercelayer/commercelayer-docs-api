---
description: How to delete an existing tax category via API
---

# Delete a tax category

To delete a tax category, send a `DELETE` request to the `/api/tax_categories/:id` endpoint, where `id` is the id of the tax category that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/tax_categories/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the tax category identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/tax_categories/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

