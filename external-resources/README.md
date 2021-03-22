---
description: How to manage resources via external serverless functions
---

# External resources

Commerce Layer lets you manage some resources \(i.e. prices, promotions, payment gateways, and more to come\) from the outside of the platform itself, using an external service of your choice or a serverless function.

In order to get the data from the external source, when needed, we trigger a `POST` request to the endpoint that you specified. The request contains a JSON payload that will be detailed case by case, along with the successful response \(or error\) format we expect to receive back. 

When you create a new external resource, a **shared secret** is generated. It will be used each time we send data to the specified endpoint to sign the payload. The signature will be stored in the **X-CommerceLayer-Signature** header so that you can verify the callback authenticity and consider it reliable.

{% page-ref page="../callbacks-security.md" %}

### Payload format

The request payload sent to an external endpoint has the same format that you get when fetching a resource through the REST API, with some relevant resources included.

```bash
  "data": {
    "id": "resource-id",
    "type": "resource-type",
    "links": { ... },
    "attributes": {...},
    "relationships": { ... },
    "meta": { ... }
  },
  "included": [
    {
      "id": "included-resource-id",
      "type": "included-resource-type",
      "links": { ... },
      "attributes": { ... },
      "relationships": { ... },
      "meta": { ... }
    }
    { ... }
  ]
}
```

### Response format

The response we require from the external endpoint is a JSON featuring the outcome of the operation, along with some data and error information \(if any\), based on what type of external resource is involved.

{% tabs %}
{% tab title="Success" %}
In case of success, you can add additional info by populating the response`metadata` attribute \(that information will be stored in the resource `metadata):`

```javascript
{
  "success": true,
	"data": {
	  ...
	  "metadata": {
	    "foo": "bar"
	  }
	}
}
```
{% endtab %}

{% tab title="Error" %}
In case of error, you can populate the error object with any relevant `code` and `message`:

```javascript
{
  "success": false,
  ...
  "error": {
    "code": "YOUR-ERROR-CODE",
		"message": "Your error message"
  }
}
```
{% endtab %}
{% endtabs %}

