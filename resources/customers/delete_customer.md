---
description: How to delete an existing customer via API
---

# Delete a customer

To delete a customer, send a `DELETE` request to the `/api/customers/:id` endpoint, where `id` is the id of the customer that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/customers/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the customer identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/customers/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

