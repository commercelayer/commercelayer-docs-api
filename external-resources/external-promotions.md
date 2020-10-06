---
description: How to manage custom promotions via eternal services
---

# External promotions

Besides the promotion types that are supported out-of-the-box \(percentage discount, fixed amount, free shipping, etc.\) Commerce Layer lets you integrate any kind of promotional engine as an external promotion.

{% page-ref page="../resources/external\_promotions/" %}

When an external promotion activates — i.e. its activation rules are met — Commerce Layer triggers a `POST` request to the `promotion_url` endpoint, sending the order payload \(including its line items\) in the request body. Your service response \(or error\) must match the format described in the example below.

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

### Security

When you create a new external promotion, a **shared secret** is generated. We recommend verifying the callback authenticity by signing the payload with that shared secret and comparing the result with the callback signature header.

{% page-ref page="../callbacks-security.md" %}



#### 

 

