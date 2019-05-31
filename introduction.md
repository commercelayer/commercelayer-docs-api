---
description: How to get your credentials and make the first API call
---

# Getting started

Commerce Layer is free for developers, and it will be forever. So the best way to get started is to [create an account](https://core.commercelayer.io/users/sign_up) and start building.

### 1. Create a test environment

After signup, you are prompted to create a sample organization with test data. This is the fastest way to get your feet wet and start playing with the API in test mode.

![](.gitbook/assets/flat-browser-image-placeholder.jpg)

Your sample organization gets populated with everything you need to place your first test order. Take a look at SKUs, inventory, prices, and settings to get a better idea of how it works.

### 2. Get your credentials

Once your sample organization is ready, go to _Settings → Applications_ and take note of your API credentials.

![](.gitbook/assets/flat-browser-image-placeholder.jpg)

The base endpoint is unique for your organization. The client ID, client secret, and scope can be used to authenticate your application and get an access token. Public applications can get an access token by using the client ID only, with limited permissions. 

{% hint style="info" %}
This is ideal for client side channel applications \(i.e. JavaScript\) that will use our hosted checkout instead of integrating our checkout APIs.
{% endhint %}

### 3. Get an access token

To get an access token for a public channel application, run the following in your terminal, making sure to replace your own endpoint and credentials:

```text
curl -X POST \
  http://your-brand.commercelayer.io/oauth/token \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "grant_type": "client_credentials",
  "client_id": "fb5eaa2b96c3a911602872e00c3e36d03cbeb1eac28143a1f0d7cac570d2cb1d",
  "scope": "market:1234"
}'
```

The response will look like this:

```text
{
    "access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.XXXXXXXXXX.XXXXXXXXXX",
    "token_type":"bearer",
    "expires_in":7200,
    "scope":"market:1234",
    "created_at":1536152431
  }
```

Take note of your access token and get ready for your first API call.

{% hint style="warning" %}
Your access token will expire in **2 hours**.
{% endhint %}

### 4. Make your first API call

As your first API call, you can get a list of SKUs. Run the following command in your terminal, making sure to replace the access token that you got in the previous step:

```text
curl -X GET \
    http://your-brand.commercelayer.io/api/skus \
    -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.XXXXXXXXXX.XXXXXXXXXX' \
    -H 'Content-Type: application/vnd.api+json'
```

Congratulations! 🎉   
You just made your first API call, getting a list of SKUs from your account. 

Now, take the time to explore the rest of the reference, learn more about the available resources and become a pro! 🙌

