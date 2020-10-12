---
description: How to execute the authorization flow and get your access token
---

# Authorization code

The `authorization_code` grant type is used by **webapp** applications to exchange an authorization code for an access token. 

Unlike the other grant types, the `authorization_code` flow requires two steps:

1. Get an [authorization code](authorization-code.md#getting-an-authorization-code)
2. Exchange the authorization code with an [access token](authorization-code.md#getting-an-access-token)

{% hint style="warning" %}
For security reasons, authorization codes expire after **10 minutes**.
{% endhint %}

## Getting an authorization code

To get an authorization code, send a `GET` request to the `/oauth/authorize` endpoint ****with the application credentials and the response type as query parameters.

{% hint style="info" %}
The response type must be `code`.
{% endhint %}

### Request

**GET** https://yourdomain.commercelayer.io**/oauth/authorize**

### Arguments

| Query parameter | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| **client\_id** | `string` | Required | Your application `client_id` |
| **redirect\_uri** | `string` | Required | Your application `redirect_uri` |
| **scope** | `string` | Optional | Your access token scope \(market\) |
| **response\_type** | `string` | Required | `code` |

### Example

#### Webapp

{% tabs %}
{% tab title="Request" %}
The following request tries to get an authorization code, putting in scope the market identified by the number "1234":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/oauth/authorize?client_id=your-client-id&redirect_uri=https://yourdomain.com/redirect&scope=market:1234&response_type=code \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code.

If the `client_id` exists, the user is prompted to authorize the 3rd party application to access their data. After the authorization, the browser is redirected to the `redirect_uri` with a `code` parameter in the URL.
{% endtab %}
{% endtabs %}

## Getting an access token

To get an access token using the `authorization_code` grant type, send a `POST` request to the `/oauth/token` endpoint, passing the application credentials and the code you got from the previous step in the request body.

### Request

**POST** https://yourdomain.commercelayer.io**/oauth/token**

### **Arguments**

| **Body parameters** | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| **grant\_type** | `string` | Required | `authorization_code` |
| **code** | `string` | Required | The authorization code that you got from the `redirect_uri` query string |
| **client\_id** | `string` | Required | Your application `client_id` |
| **client\_secret** | `string` | Required | Your application `client_secret` |
| **redirect\_uri** | `string` | Required | Your application `redirect_uri` |
| **scope** | `string` | Optional | Your access token scope \(market\) |

### Example

#### Webapp

{% tabs %}
{% tab title="Request" %}
The following request tries to get an access token for a webapp application, using the `authorization_code` grant type with the code you got from the previous step:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/oauth/token \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "grant_type": "authorization_code",
  "code": "your-authorization-code",
  "client_id": "your-client-id",
  "client_secret": "your-client-secret",
  "redirect_uri": "https://yourdomain.com/redirect"
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning the requested access token and customer info, along with a refresh token:

```javascript
{
    "access_token": "your-access-token",
    "token_type": "bearer",
    "expires_in": 7200,
    "refresh_token": "your-refresh-token",
    "scope": "market:1234",
    "created_at": 123456789,
    "owner_id": "zxcVBnMASd",
    "owner_type": "user"
}
```

{% hint style="info" %}
The returned `scope` is the same passed as a query parameter in the request you made to get `your-authorization-code`.
{% endhint %}
{% endtab %}
{% endtabs %}

