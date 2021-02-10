---
description: How to delete an existing transaction via API
---

# Delete a transaction

To delete a transaction, send a `DELETE` request to the `/api/transactions/:id` endpoint, where `id` is the id of the transaction that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/transactions/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the transaction identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/transactions/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

