---
description: How to delete an existing coupon via API
---

# Delete a coupon

To delete a coupon, send a `DELETE` request to the `/api/coupons/:id` endpoint, where `id` is the id of the coupon that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/coupons/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the coupon identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/coupons/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

