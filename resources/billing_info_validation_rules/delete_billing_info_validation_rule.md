---
description: How to delete an existing billing info validation rule via API
---

# Delete a billing info validation rule

To delete a billing info validation rule, send a `DELETE` request to the `/api/billing_info_validation_rules/:id` endpoint, where `id` is the id of the billing info validation rule that you want to delete.

{% page-ref page="../../deleting-resources.md" %}

## Request

**DELETE** https://<i></i>yourdomain.commercelayer.io**/api/billing_info_validation_rules/:id**

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to delete the billing info validation rule identified by the ID "xYZkjABcde":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/billing_info_validation_rules/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

