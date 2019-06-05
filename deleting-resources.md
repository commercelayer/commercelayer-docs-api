---
description: How to delete a resource via API
---

# Deleting resources

You can delete a resource by sending a `DELETE` request to the resource endpoint.

{% api-method method="delete" host="https://your-brand.commercelayer.io" path="/api/skus/1234" %}
{% api-method-summary %}
Delete a resource
{% endapi-method-summary %}

{% api-method-description %}
This request deletes the resource identified by the ID "1234".
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authentication" type="string" required=true %}
`Bearer {{access_token}}`
{% endapi-method-parameter %}

{% api-method-parameter name="Accept" type="string" required=false %}
`application/vnd.api+json`
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}
On success, the API returns no content.
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

