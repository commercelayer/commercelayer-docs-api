---
description: How to execute the authorization flow and get your access token
---

# Refresh token

The `refresh_token` grant type is used by clients to exchange a refresh token for an expired access token. 

**Channel** applications can use the `refresh_token` grant type to refresh a customer's access token with a "remember me" option.

## Getting an access token

To get an access token using the `refresh_token` grant type, send a `POST` request to the `/oauth/token` endpoint, passing the application credentials in the request body.

### Request

**POST** https://yourdomain.commercelayer.io**/oauth/token**

### Arguments

| Body parameter | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| **grant\_type** | `string` | Required | `refresh_token` |
| **refresh\_token** | `string` | Required | A valid `refresh_token` |
| **client\_id** | `string` | Required | Your application `client_id` |
| **client\_secret** | `string` | Optional | Your application `client_secret` |

### Example

{% tabs %}
{% tab title="Request" %}
The following request tries to exchange a valid refresh token for an expired access token:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/oauth/token \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "grant_type": "refresh_token",
  "refresh_token": "your-refresh-token",
  "client_id": "your-client-id",
  "client_secret": "your-client-secret"
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning the requested access token and customer info:

```javascript
{
    "access_token": "your-access-token",
    "token_type": "bearer",
    "expires_in": 7200,
    "refresh_token": "your-new-refresh-token",
    "scope": "market:1234",
    "created_at": 123456789,
    "owner_id": "zxcVBnMASd",
    "owner_type": "customer"
}
```

{% hint style="info" %}
The returned `scope` is the same passed in the request you made to get `your-refresh-token`.
{% endhint %}
{% endtab %}
{% endtabs %}

