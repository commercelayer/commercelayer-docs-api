---
description: How to delete a resource via API
---

# Deleting resources

You can delete a resource by sending a `DELETE` request to the resource endpoint.

{% page-ref page="authentication/" %}

### Example

{% tabs %}
{% tab title="Request" %}
The following request deletes the resource identified by the ID "1234":

```javascript
curl -X DELETE \
  https://yourdomain.commercelayer.io/api/skus/1234 \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `204 No Content` status code.
{% endtab %}
{% endtabs %}

