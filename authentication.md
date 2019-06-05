---
description: 'How to get your access token, based on OAuth 2.0 grants'
---

# Authentication

All API requests must be authenticated. To get authorized, you must include a valid access token in the `Authorization` header:

```http
Authorization: Bearer {{access_token}}
```

To get an access token, you need to execute an authorization flow by using a valid application as the client. 

{% page-ref page="applications.md" %}

The authorization flow depends on the [grant type](https://oauth.net/2/grant-types/) as described in the table below:

|  | Channel | Integration | Webapp |
| :--- | :--- | :--- | :--- |
| **Client credentials** | ✅ | ✅ |  |
| **Password** | ✅ |  |  |
| **Refresh token** | ✅ |  | ✅ |
| **Authorization code** | \*\*\*\* |  | ✅ |

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
{% api-method-parameter name="Content-Type" type="string" required=true %}
`application/json`
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
Channel applications don't use the `client_secret` parameter.
{% endhint %}

{% hint style="info" %}
The access token scope is a string composed by `"market:{{market_id}}"`
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

The `password` grant type is used by channel applications to exchange a customer's credentials for an access token, i.e., to get a "logged" access token.

{% api-method method="post" host="https://core.commercelayer.io" path="/oauth/token" %}
{% api-method-summary %}
Get an access token
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
`application/json`
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="grant\_type" type="string" required=true %}
The OAuth 2.0 grant
{% endapi-method-parameter %}

{% api-method-parameter name="username" type="string" required=true %}
The customer email address
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=true %}
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

### Refresh token

The `refresh_token` grant type is used by clients to exchange a refresh token for an expired access token. Channel applications can use the `refresh_token` grant type to refresh a customer's access token with a "remember me" option.

{% api-method method="post" host="https://core.commercelayer.io" path="/oauth/token" %}
{% api-method-summary %}
Get an access token
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
`application/json`
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="grant\_type" type="string" required=true %}
The OAuth 2.0 grant
{% endapi-method-parameter %}

{% api-method-parameter name="refresh\_token" type="string" required=true %}
A valid `refresh_token`
{% endapi-method-parameter %}

{% api-method-parameter name="client\_id" type="string" required=true %}
Your application `client_id`
{% endapi-method-parameter %}

{% api-method-parameter name="client\_secret" type="string" required=false %}
Your application `client_secret`
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
  "refresh_token": "95342a5d8d4e47b28dca8a3cbff1791b620baa344e514eafc3b87c0ce9d5f1ac",
  "owner_type": "customer",
  "owner_id": 1234,
  "created_at": 1531157026,
  "expires_in": 1531164226
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Example request

```javascript
{
  "grant_type": "refresh_token",
  "refresh_token": "c0eac0f4b2c051a1696d08b32d3f9b4de36828db3a3c5a5cabd0e8241b34a422",
  "client_id": "6a38ccf37a944d7d1bf7ddea4d231f3bf5c7534fd5d7c3f43252e6c53e40d6cc",
  "client_secret": "d47681850ffcaa01435868adfaad6755e6d11cb0e3043133db12ab743205f960"
}
```

### Authorization code

The `authorization_code` grant type is used by webapp applications to exchange an authorization code for an access token. Unlike the other grant types, the `authorization_code` flow requires two steps:

1. Get an authorization code
2. Exchange the authorization code with an access token

{% api-method method="get" host="https://core.commercelayer.io" path="/oauth/authorize" %}
{% api-method-summary %}
Get an authorization code
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
`application/json`
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="client\_id" type="string" required=true %}
Your application `client_id`
{% endapi-method-parameter %}

{% api-method-parameter name="redirect\_uri" type="string" required=true %}
Your application `redirect_uri`
{% endapi-method-parameter %}

{% api-method-parameter name="scope" type="string" required=false %}
Your access token scope \(market\)
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Example request

```text
GET /oauth/authorize?client_id=&redirect_uri=&scope=&response_type=code
```

{% api-method method="post" host="https://core.commercelayer.io" path="/oauth/token" %}
{% api-method-summary %}
Get an access token
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
`application/json`
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="grant\_type" type="string" required=true %}
The OAuth 2.0 grant
{% endapi-method-parameter %}

{% api-method-parameter name="code" type="string" required=true %}
The authorization code that you got from the `redirect_uri` query string
{% endapi-method-parameter %}

{% api-method-parameter name="client\_id" type="string" required=true %}
Your application `client_id`
{% endapi-method-parameter %}

{% api-method-parameter name="client\_secret" type="string" required=true %}
Your application `client_secret`
{% endapi-method-parameter %}

{% api-method-parameter name="redirect\_uri" type="string" required=true %}
Your application `redirect_uri`
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
  "owner_type": "user",
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
  "grant_type": "authorization_code",
  "code": "8257e65c97202ed1726cf9571600918f3bffb2544b26e00a61df9897668c33a1",
  "client_id": "6a38ccf37a944d7d1bf7ddea4d231f3bf5c7534fd5d7c3f43252e6c53e40d6cc",
  "client_secret": "d47681850ffcaa01435868adfaad6755e6d11cb0e3043133db12ab743205f960",
  "redirect_uri": "https://yourdomain.com/oauth/redirect",
  "scope": "market:1234"
}
```

