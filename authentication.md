---
description: 'How to get your access token, based on OAuth 2.0 grants'
---

# Authentication

All API requests must be authenticated. To get authorized, you must include a valid access token in the `Authorization` header:

```text
Authorization: Bearer {{access_token}}
```

To get an access token, you need to execute an authorization flow by using a valid application as the client. 

{% page-ref page="applications.md" %}

The authorization flow depends on the [grant type](https://oauth.net/2/grant-types/) as described in the table below:

|  | Channel | Integration | Webapp |
| :--- | :--- | :--- | :--- |
| Client credentials | ✅ | ✅ |  |
| Password | ✅ |  |  |
| Authorization code |  |  | ✅ |
| Refresh token | ✅ |  | ✅ |

{% hint style="warning" %}
For security reasons, access tokens expire after **2 hours**. Refresh tokens expire after **2 weeks**.
{% endhint %}

### Client credentials

Channel applications use the `client_credentials` grant type to get a "guest" access token. Integration applications use the `client_credentials` grant type to get an access token for themselves. By including a market scope in the access token request, all the resources \(e.g., SKUs, prices, stock items\) that you fetch are automatically filtered.

{% api-method method="post" host="https://core.commercelayer.io" path="/oauth/token" %}
{% api-method-summary %}
Get an access token
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Access" type="string" required=false %}
application/json
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=false %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="grant\_type" type="string" required=true %}
The OAuth 2.0 grant
{% endapi-method-parameter %}

{% api-method-parameter name="client\_id" type="string" required=true %}
Your application `client_id`
{% endapi-method-parameter %}

{% api-method-parameter name="client\_secret" type="string" required=false %}
Your application `client_secret`, not used by public channel application
{% endapi-method-parameter %}

{% api-method-parameter name="scope" type="string" required=false %}
Your access token scope \(market\)
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "token_type": "bearer",
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.XXXXXXXXXX.XXXXXXXXXX",
  "scope": "market:1234",
  "refresh_token": nil,
  "created_at": 1531156632,
  "expires_in": 1531163832
}

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
The access token scope is a string composed by `"market:" + market_id`
{% endhint %}

#### Example request

```javascript
{
  "grant_type": "client_credentials",
  "client_id": "6a38ccf37a944d7d1bf7ddea4d231f3bf5c7534fd5d7c3f43252e6c53e40d6cc",
  "client_secret": "d47681850ffcaa01435868adfaad6755e6d11cb0e3043133db12ab743205f960",
  "scope": "market:1234"
}
```

### Password

The Password grant type is used by channel applications to exchange a customer's credentials for an access token, i.e., to get a "logged" access token.

{% api-method method="post" host="https://core.commercelayer.io" path="/oauth/token" %}
{% api-method-summary %}
Get an access token
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Access" type="string" required=false %}
application/json
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=false %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="grant\_type" type="string" required=true %}
The OAuth 2.0 grant
{% endapi-method-parameter %}

{% api-method-parameter name="username" type="string" required=true %}
The customer email address
{% endapi-method-parameter %}

{% api-method-parameter name="customer\_password" type="string" required=true %}
The customer password
{% endapi-method-parameter %}

{% api-method-parameter name="client\_id" type="string" required=true %}
Your application `client_id`
{% endapi-method-parameter %}

{% api-method-parameter name="client\_secret" type="string" required=false %}
Your application `client_secret`
{% endapi-method-parameter %}

{% api-method-parameter name="scope" type="string" required=false %}
Your access token scope \(market\)
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "token_type": "bearer",
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.XXXXXXXXXX.XXXXXXXXXX",
  "scope": "market:1234",
  "refresh_token": "6426f54e7b3f1713e641ba51ab93b0f18a5aa1cf002bb0db5df82219775e2707",
  "owner_type": "customer",
  "owner_id": 1234,
  "created_at": 1531156632,
  "expires_in": 1531163832
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Example request

```javascript
{
  "grant_type": "password",
  "username": "jonh@example.com",
  "password": "secret",
  "client_id": "6a38ccf37a944d7d1bf7ddea4d231f3bf5c7534fd5d7c3f43252e6c53e40d6cc",
  "client_secret": "d47681850ffcaa01435868adfaad6755e6d11cb0e3043133db12ab743205f960",
  "scope": "market:1234"
}
```

