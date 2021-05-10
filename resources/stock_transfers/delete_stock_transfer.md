---
description: How to delete an existing stock transfer via API
---

# Delete a stock transfer

To delete a stock transfer, send a `DELETE` request to the `/api/stock_transfers/:id` endpoint, where `id` is the id of the stock transfer that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/stock_transfers/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the stock transfer identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/stock_transfers/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

