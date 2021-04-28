---
description: How to delete an existing order amount promotion rule via API
---

# Delete an order amount promotion rule

To delete an order amount promotion rule, send a `DELETE` request to the `/api/order_amount_promotion_rules/:id` endpoint, where `id` is the id of the order amount promotion rule that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/order_amount_promotion_rules/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the order amount promotion rule identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/order_amount_promotion_rules/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

