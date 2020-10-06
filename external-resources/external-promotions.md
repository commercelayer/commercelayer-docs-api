---
description: How to manage custom promotions via serverless functions
---

# External promotions

Commerce Layer lets you build your own outside lambda function to calculate complete custom promotions, based on the order information.

{% page-ref page="../resources/external\_promotions/" %}

Whenever the external promotion is fired — according to the activation rules you set up when you created it — a `POST` request is triggered to the endpoint that you specified in the `promotion_url` field. 

### Example

{% tabs %}
{% tab title="Payload" %}
The request payload contains the order and includes its line items

```javascript
{
  "data": {
    "id": "wBXVhKzrnq",
    "type": "orders",
    "links": { ... },
    "attributes": { ... },
    "relationships": { ... },
    "meta": { ... }
  },
  "included": [
    {
      "id": "kJbZtxWVBm",
      "type": "line_items",
      "links": { ... },
      "attributes": { ... },
      "relationships": { ... },
      "meta": { ... }
    },
    {
      "id": "yQjYtnzxzj",
      "type": "line_items",
      "links": { ... },
      "attributes": { ... },
      "relationships": { ... },
      "meta": { ... }
    },
    { ... }
  ]
}
```
{% endtab %}

{% tab title="Response" %}
The successful response must be a JSON object, returning the discount computed by the external logic, along with some additional information and metadata:

```javascript
{
  "success": "true",
  "data": {
    "name": "My External Promotion",
    "discount_cents": 1500,
    "metadata": {
      "foo": "bar"
    }
  }
}
```
{% endtab %}

{% tab title="Error" %}
On error, the response must be a JSON object containing an error code and an error message:

```javascript
{
  "success": "false",
  "error": {
    "code": "YOUR-ERROR-CODE",
    "message": "Your error message"
  }
}
```
{% endtab %}
{% endtabs %}

#### 

 

