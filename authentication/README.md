---
description: 'How to get your access token, based on OAuth 2.0 grants'
---

# Authentication

All API requests must be authenticated. To get authorized, you must include a valid access token in the **Authorization** header:

```http
Authorization: Bearer your-access-token
```

### Authorization flows

To get an access token, you need to execute an authorization flow by using a valid application as the client. 

The authorization flow depends on the [grant type](https://oauth.net/2/grant-types/) as described in the table below:

| Grant type | Sales channel | Integration | Webapp |
| :--- | :--- | :--- | :--- |
| **Client credentials** | \*\*\*\*✅ | ✅ |  |
| **Password** | ✅ |  |  |
| **Refresh token** | \*\*\*\*✅ |  | ✅ |
| **Authorization code** | \*\*\*\* |  | ✅ |

{% hint style="warning" %}
For security reasons, access tokens expire after **2 hours**.
{% endhint %}

