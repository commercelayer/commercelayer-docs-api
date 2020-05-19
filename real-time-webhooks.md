---
description: The complete list of supported events for each resource
---

# Real-time webhooks

Commerce Layer provides a [webhook](https://en.wikipedia.org/wiki/Webhook) mechanism to react to specific events in real-time. 

Each time a subscribed event occurs, we trigger a `POST` request to the endpoint that you specified in the `callback_url` field. The request contains a JSON payload in the same format that you get when fetching the same resource through the REST API. 

{% page-ref page="fetching-resources.md" %}

For each resource, you can also configure the related resources that should be included in the request body. The relationships will be set as the resource `include` query parameter.

{% page-ref page="including-associations.md" %}

When you create a new webhook, a **shared secret** is generated. It will be used each time the webhook is fired to sign the payload. The related signature will be stored in the **X-CommerceLayer-Signature** header so that you can [verify the callback authenticity](real-time-webhooks.md#verifying-the-callback-authenticity) and consider it reliable.

### Supported events

You can find here below the complete list of all the topics `{{resource}}.{{event}}` you can monitor:

| Topic | Trigger |
| :--- | :--- |
| customer\_password\_resets.**create** | A customer password reset process is initiated |
| customer\_password\_resets.**destroy** | An existing `customer_password_resets` object is deleted |
| customer\_subscriptions.**create** | A new customer subscription is created |
| customer\_subscriptions.**destroy** | An existing `customer_subscriptions` object is deleted |
| customers.**create** | A new customer is created |
| customers.**acquired**  | An existing customer status is set to `acquired` |
| customers.**repeat** | An existing customer status is set to `repeat` |
| customers.**destroy** | An existing `customers` object is deleted |
| imports.**create** | A new import is created |
| imports.**start**  | An existing import status is set to `started` |
| imports.**complete**  | An existing import status is set to `completed` |
| imports.**destroy** | An existing `imports` object is deleted |
| orders.**create** | A new order is created |
| orders.**draft**  | An existing order status is set to `draft` |
| orders.**pending** | An existing order status is set to `pending` |
| orders.**place** | An existing order status is set to `placed` |
| orders.**approve** | An existing order status is set to `approved` |
| orders.**cancel** | An existing order status is set to `cancelled` |
| orders.**authorize** | An existing order payment status is set to `authorized` |
| orders.**void**  | An existing order payment status is set to `voided` |
| orders.**pay** | An existing order payment status is set to `paid` |
| orders.**refund** | An existing order payment status is set to `refunded` |
| orders.**start\_fulfilling**  | An existing order fulfillment status is set to `in_progress` |
| orders.**fulfill** | An existing order fulfillment status is set to `fulfilled` |
| orders.**destroy** | An existing `orders` object is deleted |
| parcels.**create**  | A new parcel is created |
| parcels.**destroy** | An existing orders `parcels` object is deleted |
| shipments.**create** | A new shipment is created |
| shipments.**upcoming**  | An existing shipment status is set to `upcoming` |
| shipments.**cancel** | An existing shipment status is set to `cancelled` |
| shipments.**on\_hold** | An existing shipment status is set to `on_hold` |
| shipments.**picking** | An existing shipment status is set to `picking` |
| shipments.**packing**  | An existing shipment status is set to `packing` |
| shipments.**ready\_to\_ship** | An existing shipment status is set to `ready_to_ship` |
| shipments.**ship** | An existing shipment status is set to `shipped` |
| shipments.**destroy** | An existing `shipments` object is deleted |

{% hint style="info" %}
The endpoint listening for webhooks has **5 seconds** to respond with a `2xx` response \(usually `204` or `200` \) and acknowledge successful delivery. If the request times out \(or the target application or API responds with an HTTP status code other than `2xx`\) we consider the request as failed.
{% endhint %}

### Verifying the callback authenticity

For security reasons, we recommend verifying the callback authenticity by signing the payload with the shared secret \([SHA256 HMAC](https://en.wikipedia.org/wiki/HMAC)\) and comparing the result with the **X-CommerceLayer-Signature** callback header. In details:

1. Read the **X-CommerceLayer-Signature** header and get the encrypted signature.
2. Rebuild the signature according to the SHA256 HMAC algorithm, using the payload body and the webhook shared secret.
3. Compare your signature with the one you got from the header.
4. If the two signatures match, you can proceed safely — if not, you can't trust the callback.

#### Example

This is a sample script in **Node.js** that you can use as a reference to check the webhook signature:

```javascript
import CryptoJS from 'crypto-js'
import hmacSHA256 from 'crypto-js/hmac-sha256'

export default (req, res) => {
  const signature = req.headers['x-commercelayer-signature']
  const hash = hmacSHA256(JSON.stringify(req.body), process.env.SHARED_SECRET)
  const encode = hash.toString(CryptoJS.enc.Base64)
  if (req.method === 'POST' && signature === encode) {
		// your-code
    res.status(200).json({
      success: true,
    })
  } else {
    res.status(401).json({
      error: 'Unauthorized',
    })
  }
}
```

{% hint style="warning" %}
When verifying the callback authenticity, make sure to read the **raw body** of the payload and NOT the parsed one.
{% endhint %}

