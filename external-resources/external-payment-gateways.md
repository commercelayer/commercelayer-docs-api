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

{% hint style="info" %}
External gateways process payments **synchronously** by default. If you need your gateway to behave differently, check the [asynchronous payments section](external-payment-gateways.md#asynchronous-payments).
{% endhint %}

### Request

The request payload is a [JSON:API](https://jsonapi.org/) compliant object you can query to perform your own computation. Aside from the **target resource** — which depends on the kind of gateway's transaction — some **relationships** are also included to avoid useless API roundtrips:

* `order`
* `order.market`
* `order.line_items`
* `order.line_items.item`
* `order.shipping_address`
* `order.billing_address`

```javascript
{
  "data": {
    ...
  },
  "included": [
    {
      "id": "wBXVhKzrnq",
      "type": "orders",
      "links": { ... },
      "attributes": { ... },
      "relationships": { ... },
      "meta": { ... }
    },
    {
      "id": "DvlGRmhdgX",
      "type": "markets",
      "links": { ... },
      "attributes": { ... },
      "relationships": { ... },
      "meta": { ... }
    },
    {
      "id": "kdPgtRXOKL",
      "type": "line_items",
      "links": { ... },
      "attributes": { ... },
      "relationships": { ... },
      "meta": { ... }
    },
    {
      "id": "XGZwpOSrWL",
      "type": "skus",
      "links": { ... },
      "attributes": { ... },
      "relationships": { ... },
      "meta": { ... }
    }
    {
      "id": "BgnguJvXmb",
      "type": "addresses",
      "links": { ... },
      "attributes": { ... },
      "relationships": { ... },
      "meta": { ... }
    },
    {
      "id": 'AlrkugwyVW',
      "type": 'addresses',
      "links": { ... },
      "attributes": { ... },
      "relationships": { ... },
      "meta": { ... }
    },
    { ... }
  ]
}
```

### Authorization

When you place an order, Commerce Layer triggers a `POST` request to the endpoint that you specified in the `authorize_url` field and creates an authorization.

{% page-ref page="../resources/authorizations/" %}

#### Example

{% tabs %}
{% tab title="Payload" %}
The request payload contains the external payment resource and includes the [above-mentioned](external-payment-gateways.md#request) relationships:

```javascript
{
  "data": {
    "id": "ZNKjeUYepv",
    "type": "external_payments",
    "links": { ... },
    "attributes": { ... },
    "relationships": { ... },
    "meta": { ... }
  },
  "included": [
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
The request payload contains the authorization resource and includes the [above-mentioned](external-payment-gateways.md#request) relationships:

```javascript
{
  "data": {
    "id": "yGzeUJxRJj",
    "type": "authorizations",
    "links": { ... },
    "attributes": { ... },
    "relationships": { ... },
    "meta": { ... }
  },
  "included": [
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
The request payload contains the authorization resource and includes the [above-mentioned](external-payment-gateways.md#request) relationships:

```javascript
{
  "data": {
    "id": "yGzeUJxRJj",
    "type": "authorizations",
    "links": { ... },
    "attributes": { ... },
    "relationships": { ... },
    "meta": { ... }
  },
  "included": [
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
The request payload contains the capture resource and includes the [above-mentioned](external-payment-gateways.md#request) relationships:

```javascript
{
  "data": {
    "id": "yJQDUVndWj",
    "type": "captures",
    "links": { ... },
    "attributes": { ... },
    "relationships": { ... },
    "meta": { ... }
  },
  "included": [
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

### Asynchronous payments

It might be the case you don't want your gateway to process payments immediately.  That's why Commerce Layer provides the option to mark your external gateway response as **asynchronous** and expose a `webhook_endpoint_url` you can call once the payment status changes.

#### Action ID

A payment is marked as asynchronous when the following conditions on the response to any of the external payment gateway transactions are met:

* HTTP code is `202`
* It contains the `action_id` key, which _uniquely_ identifies the related transaction

{% hint style="info" %}
`action_id` uniqueness is mandatory for the [webhook](external-payment-gateways.md#webhook-endpoint) to detect the transaction later.
{% endhint %}

In this case, the external payment gateway creates the transaction setting the `succeeded` attribute to `false`, but considering it as pending. This way, the order can be placed without errors, but the order payment status doesn't change yet \(even if the order is not editable anymore\).

#### Example

{% tabs %}
{% tab title="Payload" %}
The payload requested by the related transaction, as explained in the [authorization](external-payment-gateways.md#authorization), [capture](external-payment-gateways.md#capture), [void](external-payment-gateways.md#void), and [refund](external-payment-gateways.md#refund) sections.
{% endtab %}

{% tab title="Response" %}
The successful response must be a JSON object, returning a transaction token \(e.g. the one provided by the payment gateway\), the amount involved, and the unique identifier of the transaction. If needed, you can add some metadata that will be copied into the related transaction resource that is being created:

```javascript
{
  "success": true,
  "data": {
    "transaction_token": "your-external-transaction-token",
    "amount_cents": 12900,
    "action_id": "your-action-id"
    "metadata": {
      "foo": "bar"
    }
  }
}
```
{% endtab %}

{% tab title="Error" %}
On error, the response must be a JSON object containing a transaction token \(e.g. the one provided by the payment gateway\) and the amount involved in the transaction, along with an error code and an error message:

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

#### Webhook endpoint

To notify the payment has changed its status, the external gateway exposes a `webhook_endpoint_url` you can call accordingly once the related payment transaction gets an update, as long as you follow these requirements:

* It accepts only POST requests
* You must include an **X-CommerceLayer-Signature** header, which contains the [HMAC](https://en.wikipedia.org/wiki/HMAC) of the request payload signed with a **SHA256** algorithm and the same [shared secret](external-payment-gateways.md#security) already exposed by the external payment gateway
* The request body must have the same structure as the response — a JSON object with the attributes you need to update the transaction with — and include the `action_id` previously used 

The external payment gateway will use this data to fetch the pending transaction and update the attributes with the new values. On successful update, the transaction `succeeded` attribute is set to `true` and the order is updated to the right status — `authorized`, `paid`, `voided`, or `refunded`. On error, the order status remains as it is.

#### Updatable attributes

Only a subset of attributes is allowed for an update, assuming the main ones have already been set by [the first async response](external-payment-gateways.md#action-id) \(e.g. `amount_cents` and `transaction_token` cannot be updated\). The updatable transaction fields are:

* `message`
* `error_code`
* `error_detail`
* `avs_code`
* `avs_message`
* `cvv_code`
* `cvv_message`
* `fraud_review`

### Security

When you create a new external payment gateway, a **shared secret** is generated. We recommend verifying the callback authenticity by signing the payload with that shared secret and comparing the result with the callback signature header.

{% page-ref page="../callbacks-security.md" %}

