---
description: How to delete an existing customer payment source via API
---

# Delete a customer payment source

To delete a customer payment source, send a `DELETE` request to the `/api/customer_payment_sources/:id` endpoint, where `id` is the id of the customer payment source that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://yourdomain.commercelayer.io**/api/customer_payment_sources/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the customer payment source identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/customer_payment_sources/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

