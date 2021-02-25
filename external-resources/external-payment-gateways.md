---
description: How to manage payments and transactions via external services
---

# External payment gateways

Commerce Layer is integrated with some of the most popular payment gateways — **Stripe**, **Adyen**, **Braintree**, **Paypal**. They are all compliant with the PSD2 European regulation so that you can implement a payment flow that supports SCA and 3DS2.

Adding new payment gateways to our core is already provided for in our roadmap. Anyway, you already have the complete flexibility to connect whichever payment service provider you may need. To do that, just create an external payment gateway and define your custom endpoint\(s\) responding to the following transaction types:

1. [Authorization](external-payment-gateways.md#authorization) — to authorize a payment source
2. [Capture](external-payment-gateways.md#capture) — to capture an authorization
3. [Void](external-payment-gateways.md#void) — to void an authorization
4. [Refund](external-payment-gateways.md#refund) — to refund a capture, either totally or partially

Your external endpoint will be responsible for the actual integration with the payment gateway. The payment source associated with the order must be an external payment.

{% page-ref page="../resources/external\_payments/" %}

### Authorization

When you place an order, Commerce Layer triggers a `POST` request to the endpoint that you specified in the `authorize_url` field and creates an authorization.

{% page-ref page="../resources/authorizations/" %}

#### Example

{% tabs %}
{% tab title="Payload" %}
The request payload contains the external payment source and includes the associated `order`, `order.line_items`, `order.shipping_address`, and `order.billing_address`:

```javascript
{
  data: {
    id: 'ZNKjeUYepv',
    type: 'external_payments',
    links: { ... },
    attributes: { ... },
    relationships: { ... },
    meta: { ... }
  },
  included: [
    {
      id: 'wBXVhKzrnq',
      type: 'orders',
      links: { ... },
      attributes: { ... },
      relationships: { ... },
      meta: { ... }
    },
    {
      id: 'BgnguJvXmb',
      type: 'addresses',
      links: { ... },
      attributes: { ... },
      relationships: { ... },
      meta: { ... }
    },
    {
      id: 'AlrkugwyVW',
      type: 'addresses',
      links: { ... },
      attributes: { ... },
      relationships: { ... },
      meta: { ... }
    },
    {
      id: 'kdPgtRXOKL',
      type: 'line_items',
      links: { ... },
      attributes: { ... },
      relationships: { ... },
      meta: { ... }
    },
    { ... }
  ]
}
```
{% endtab %}

{% tab title="Response" %}
The successful response must be a JSON object, returning a transaction token \(e.g. the one provided by the payment gateway\) and the total amount that has been authorized. If needed, you can add some metadata that will be copied into the authorization resource that is being created:

```javascript
{
  "success": true,
  "data": {
    "transaction_token": "your-external-transaction-token",
    "amount_cents": 12900,
    "metadata": {
      "foo": "bar"
    }
  }
}
```
{% endtab %}

{% tab title="Error" %}
On error, the response must be a JSON object containing a transaction token \(e.g. the one provided by the payment gateway\) and the authorization amount, along with an error code and an error message:

```javascript
{
  "success": false,
  "data": {
    "transaction_token": "your-external-transaction-token",
    "amount_cents": 12900,
    "error": {
      "code": "YOUR-ERROR-CODE",
      "message": "Your error message"
    }
  }
}
```
{% endtab %}
{% endtabs %}

### Capture

When you try to capture an authorization, Commerce Layer triggers a `POST` request to the endpoint that you specified in the `capture_url` field and creates a capture.

{% page-ref page="../resources/captures/" %}

#### Example

{% tabs %}
{% tab title="Payload" %}
The request payload contains the authorization and includes the associated `order`, `order.line_items`, `order.shipping_address`, and `order.billing_address`:

```javascript
{
  data: {
    id: 'yGzeUJxRJj',
    type: 'authorizations',
    links: { ... },
    attributes: { ... },
    relationships: { ... },
    meta: { ... }
  },
  included: [
    {
      id: 'wBXVhKzrnq',
      type: 'orders',
      links: { ... },
      attributes: { ... },
      relationships: { ... },
      meta: { ... }
    },
    {
      id: 'BgnguJvXmb',
      type: 'addresses',
      links: { ... },
      attributes: { ... },
      relationships: { ... },
      meta: { ... }
    },
    {
      id: 'AlrkugwyVW',
      type: 'addresses',
      links: { ... },
      attributes: { ... },
      relationships: { ... },
      meta: { ... }
    },
    {
      id: 'kdPgtRXOKL',
      type: 'line_items',
      links: { ... },
      attributes: { ... },
      relationships: { ... },
      meta: { ... }
    },
    { ... }
  ]
}
```
{% endtab %}

{% tab title="Response" %}
The successful response must be a JSON object, returning a transaction token \(e.g. the one provided by the payment gateway\) and the total amount that has been captured. If needed, you can add some metadata that will be copied into the capture resource that is being created:

```javascript
{
  "success": true,
  "data": {
    "transaction_token": "your-external-transaction-token",
    "amount_cents": 12900,
    "metadata": {
      "foo": "bar"
    }
  }
}
```
{% endtab %}

{% tab title="Error" %}
On error, the response must be a JSON object containing a transaction token \(e.g. the one provided by the payment gateway\) and the capture amount, along with an error code and an error message:

```javascript
{
  "success": false,
  "data": {
    "transaction_token": "your-external-transaction-token",
    "amount_cents": 12900,
    "error": {
      "code": "YOUR-ERROR-CODE",
      "message": "Your error message"
    }
  }
}
```
{% endtab %}
{% endtabs %}

### Void

When you try to void an authorization, Commerce Layer triggers a `POST` request to the endpoint that you specified in the `void_url` field and creates a void.

{% page-ref page="../resources/voids/" %}

#### Example

{% tabs %}
{% tab title="Payload" %}
The request payload contains the authorization and includes the associated `order`, `order.line_items`, `order.shipping_address`, and `order.billing_address`:

```javascript
{
  data: {
    id: 'yGzeUJxRJj',
    type: 'authorizations',
    links: { ... },
    attributes: { ... },
    relationships: { ... },
    meta: { ... }
  },
  included: [
    {
      id: 'wBXVhKzrnq',
      type: 'orders',
      links: { ... },
      attributes: { ... },
      relationships: { ... },
      meta: { ... }
    },
    {
      id: 'BgnguJvXmb',
      type: 'addresses',
      links: { ... },
      attributes: { ... },
      relationships: { ... },
      meta: { ... }
    },
    {
      id: 'AlrkugwyVW',
      type: 'addresses',
      links: { ... },
      attributes: { ... },
      relationships: { ... },
      meta: { ... }
    },
    {
      id: 'kdPgtRXOKL',
      type: 'line_items',
      links: { ... },
      attributes: { ... },
      relationships: { ... },
      meta: { ... }
    },
    { ... }
  ]
}
```
{% endtab %}

{% tab title="Response" %}
The successful response must be a JSON object, returning a transaction token \(e.g. the one provided by the payment gateway\) and the total amount that has been voided. If needed, you can add some metadata that will be copied into the void resource that is being created:

```javascript
{
  "success": true,
  "data": {
    "transaction_token": "your-external-transaction-token",
    "amount_cents": 12900,
    "metadata": {
      "foo": "bar"
    }
  }
}
```
{% endtab %}

{% tab title="Error" %}
On error, the response must be a JSON object containing a transaction token \(e.g. the one provided by the payment gateway\) and the void amount, along with an error code and an error message:

```javascript
{
  "success": false,
  "data": {
    "transaction_token": "your-external-transaction-token",
    "amount_cents": 12900,
    "error": {
      "code": "YOUR-ERROR-CODE",
      "message": "Your error message"
    }
  }
}
```
{% endtab %}
{% endtabs %}

### Refund

When you try to void a capture, Commerce Layer triggers a `POST` request to the endpoint that you specified in the `refund_url` field and creates a refund.

{% page-ref page="../resources/refunds/" %}

#### Example

{% tabs %}
{% tab title="Payload" %}
The request payload contains the capture and includes the associated `order`, `order.line_items`, `order.shipping_address`, and `order.billing_address`:

```javascript
{
  data: {
    id: 'yJQDUVndWj',
    type: 'captures',
    links: { ... },
    attributes: { ... },
    relationships: { ... },
    meta: { ... }
  },
  included: [
    {
      id: 'wBXVhKzrnq',
      type: 'orders',
      links: { ... },
      attributes: { ... },
      relationships: { ... },
      meta: { ... }
    },
    {
      id: 'BgnguJvXmb',
      type: 'addresses',
      links: { ... },
      attributes: { ... },
      relationships: { ... },
      meta: { ... }
    },
    {
      id: 'AlrkugwyVW',
      type: 'addresses',
      links: { ... },
      attributes: { ... },
      relationships: { ... },
      meta: { ... }
    },
    {
      id: 'kdPgtRXOKL',
      type: 'line_items',
      links: { ... },
      attributes: { ... },
      relationships: { ... },
      meta: { ... }
    },
    { ... }
  ]
}
```
{% endtab %}

{% tab title="Response" %}
The successful response must be a JSON object, returning a transaction token \(e.g. the one provided by the payment gateway\) and the amount that has been refunded. If needed, you can add some metadata that will be copied into the refund resource that is being created:

```javascript
{
  "success": true,
  "data": {
    "transaction_token": "your-external-transaction-token",
    "amount_cents": 9900,
    "metadata": {
      "foo": "bar"
    }
  }
}
```
{% endtab %}

{% tab title="Error" %}
On error, the response must be a JSON object containing a transaction token \(e.g. the one provided by the payment gateway\) and the refund amount, along with an error code and an error message:

```javascript
{
  "success": false,
  "data": {
    "transaction_token": "your-external-transaction-token",
    "amount_cents": 9900,
    "error": {
      "code": "YOUR-ERROR-CODE",
      "message": "Your error message"
    }
  }
}
```
{% endtab %}
{% endtabs %}

### Security

When you create a new external payment gateway, a **shared secret** is generated. We recommend verifying the callback authenticity by signing the payload with that shared secret and comparing the result with the callback signature header.

{% page-ref page="../callbacks-security.md" %}

