---
description: How to execute the authorization flow and get your access token
---

# Password

The `password` grant type is used by **Sales channel** applications to exchange a customer credentials for an access token \(i.e. to get a "logged" access token\).

{% hint style="info" %}
By [including a scope](./#authorization-scopes) in the access token request, all the resources that you fetch are automatically filtered.
{% endhint %}

## Getting an access token

To get an access token using the `password` grant type, send a `POST` request to the `/oauth/token` endpoint, passing the application credentials in the request body.

### Request

**POST** https://yourdomain.commercelayer.io**/oauth/token**

### Arguments

| Body parameter | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| **grant\_type** | `string` | Required | `password` |
| **username** | `string` | Required | The customer email address |
| **password** | `string` | Required | The customer password |
| **client\_id** | `string` | Required | Your application `client_id` |
| **scope** | `string` | Optional | Your access token scope \(market, stock location\) |

{% hint style="info" %}
The access token scope is a string composed by `"market:{{market_number}}"`, where `market_number` is the number of the market you want to put in scope.
{% endhint %}

### Example

#### Sales channel

{% tabs %}
{% tab title="Request" %}
The following request tries to get an access token for a sales channel application, using the `password` grant type for a specific user, putting in scope the market identified by the number "1234":

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/oauth/token \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "grant_type": "password",
  "username": "john@example.com",
  "password": "secret",
  "client_id": "your-client-id",
  "scope": "market:1234"
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning the requested access token and customer info, along with a [refresh token](refresh-token.md#sales-channel):

```javascript
{
    "access_token": "your-access-token",
    "token_type": "bearer",
    "expires_in": 7200,
    "refresh_token": "your-refresh-token",
    "scope": "market:1234",
    "created_at": 123456789,
    "owner_id": "zxcVBnMASd",
    "owner_type": "customer"
}
```
{% endtab %}
{% endtabs %}

