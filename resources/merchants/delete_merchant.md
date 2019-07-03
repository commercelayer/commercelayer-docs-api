---
description: How to delete an existing merchant via API
---

# Delete a merchant

To delete a merchant, send a `DELETE` request to the `/api/merchants/:id` endpoint, where `id` is the id of the merchant that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/merchants/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the merchant identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/merchants/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}
