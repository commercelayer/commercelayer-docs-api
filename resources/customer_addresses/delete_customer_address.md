---
description: How to delete an existing customer address via API
---

# Delete a customer address

To delete a customer address, send a `DELETE` request to the `/api/customer_addresses/:id` endpoint, where `id` is the id of the customer address that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/customer_addresses/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the customer address identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/customer_addresses/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

