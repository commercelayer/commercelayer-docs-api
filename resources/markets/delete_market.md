---
description: How to delete an existing market via API
---

# Delete a market

To delete a market, send a `DELETE` request to the `/api/markets/:id` endpoint, where `id` is the id of the market that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/markets/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the market identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/markets/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

