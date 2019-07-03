---
description: How to delete an existing credit card via API
---

# Delete a credit card

To delete a credit card, send a `DELETE` request to the `/api/credit_cards/:id` endpoint, where `id` is the id of the credit card that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/credit\_cards/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the credit card identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/credit_cards/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

