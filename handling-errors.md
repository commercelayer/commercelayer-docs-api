---
description: The complete list of response codes
---

# Handling errors

Commerce Layer uses [HTTP response codes](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) to show the success or failure of an API request. Codes in the `2xx` range indicate success. Codes in the `4xx` range indicate an error that failed given the information provided \(e.g. failed validation or authentication\). Codes in the `5xx` range indicate an unhandled error \(these are rare and should never happen\).

| Code | Message | Description |
| :--- | :--- | :--- |
| **200** | OK | The request was successfully processed and everything worked as expected. |
| **201** | Created | The request was successfully processed and a new resource was created. |
| **400** | Bad request | The request was unacceptable, often due to sending an unsupported parameter. |
| **401** | Unauthorized | The access token was not present in the request, was expired or didn't have enough permissions. |
| **404** | Not found | The requested resource was not found, often due to a wrong resource's id. |
| **405** | Method not allowed | The request method is known by the server but has been disabled and cannot be used. |
| **406** | Not acceptable | The "Accept" header was not correctly set to `application/vnd.api+json` |
| **415** | Unsupported media type | The "Content-type" header was not correctly set to `application/vnd.api+json` |
| **422** | Unprocessable entity | The request body was well-formed but contains semantical errors, often due to validation constraints. |
| **423** | Locked | The resource could not be deleted due to integrity constraints. |
| **429** | Too many requests | The request was not accepted because you hit the rate limit. |
| **500** | Internal server error | Something went wrong on our end and is being investigated by our engineers. |

### The error object

All the `4xx` responses include an error object in the response body. The object contains the list of `errors` with extra information. We recommend writing code that gracefully handles all possible API exceptions.

{% api-method method="patch" host="https://your-brand.commercelayer.io" path="/api/line\_items" %}
{% api-method-summary %}
Change an attribute
{% endapi-method-summary %}

{% api-method-description %}
This request tries to update the quantity of the line item associated to the resource identified by the ID "1234".
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
`application/vnd.api+json`
{% endapi-method-parameter %}

{% api-method-parameter name="Accept" type="string" required=false %}
`application/vnd.api+json`
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}
The API returns a validation error.
{% endapi-method-response-example-description %}

```javascript
{
  "errors": [
    {
      "title": "must be less than or equal to 10",
      "detail": "quantity - must be less than or equal to 10",
      "code": "VALIDATION_ERROR",
      "source": {
        "pointer": "/data/attributes/quantity"
      },
      "status"=>"422",
      "meta": {
        "error": "less_than_or_equal_to",
        "count": 10,
        "value": 100
      }
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Example request

```javascript
{
  "data": {
    "type": "line_items",
    "id": 1234,
    "attributes": {
      "quantity": 100
    }
  }
}
```

