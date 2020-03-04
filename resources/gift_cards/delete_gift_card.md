---
description: How to delete an existing gift card via API
---

# Delete a gift card

To delete a gift card, send a `DELETE` request to the `/api/gift_cards/:id` endpoint, where `id` is the id of the gift card that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/gift\_cards/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the gift card identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/gift_cards/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

