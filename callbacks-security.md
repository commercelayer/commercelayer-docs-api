---
description: How to verify callbacks authenticity
---

# Callbacks security

For security reasons, when sending and receiving data and information to and from an external endpoint \(i.e. [real-time webhooks](real-time-webhooks.md), [external resources](external-resources/)\) we recommend verifying the callback authenticity by signing the payload with the shared secret \([SHA256 HMAC](https://en.wikipedia.org/wiki/HMAC)\) and comparing the result with the **X-CommerceLayer-Signature** callback header. In details:

1. Read the **X-CommerceLayer-Signature** header and get the encrypted signature.
2. Rebuild the signature according to the SHA256 HMAC algorithm, using the payload body and the provided shared secret.
3. Compare your signature with the one you got from the header.
4. If the two signatures match, you can proceed safely — if not, you can't trust the callback.

#### Example

This is a sample script in **Node.js** that you can use as a reference to check the signature:

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

