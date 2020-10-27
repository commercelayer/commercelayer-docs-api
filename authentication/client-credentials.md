---
description: How to execute the authorization flow and get your access token
---

# Client credentials

**Sales channel** applications use the `client_credentials` grant type to get a "guest" access token. 

**Integration** applications use the `client_credentials` grant type to get an access token for themselves. 

{% hint style="info" %}
By including a market `scope` in the access token request, all the resources \(e.g. SKUs, prices, stock items\) that you fetch are automatically filtered.
{% endhint %}

## Getting an access token

To get an access token using the `client_credentials` grant type, send a `POST` request to the `/oauth/token` endpoint, passing the application credentials in the request body.

### Request

**POST** https://yourdomain.commercelayer.io**/oauth/token**

### Arguments

| Body parameter | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| **grant\_type** | `string` | Required | `client_credentials` |
| **client\_id** | `string` | Required | Your application `client_id` |
| **client\_secret** | `string` | Optional | Your application `client_secret` |
| **scope** | `string` | Optional | Your access token scope \(market\) |

{% hint style="info" %}
The access token scope is a string composed by `"market:{{market_number}}"`, where `market_number` is the number of the market you want to put in scope.
{% endhint %}

{% hint style="warning" %}
**Sales channel** applications don't require the `client_secret` argument.
{% endhint %}

### Examples

#### Sales channel

{% tabs %}
{% tab title="Request" %}
The following request tries to get an access token for a sales channel application, using the `client_credentials` grant type and putting in scope the market identified by the number "1234":

```bash
curl -X POST \
  https://yourdomain.commercelayer.io/oauth/token \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "grant_type": "client_credentials",
  "client_id": "your-client-id",
  "scope": "market:1234"
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning the requested access token:

```javascript
{
  "access_token": "your-access-token",
  "token_type": "bearer",
  "expires_in": 7200,
  "scope": "market:1234",
  "created_at": 123456789
}
```
{% endtab %}
{% endtabs %}

#### Integration

{% tabs %}
{% tab title="Request" %}
The following request tries to get an access token for an integration application, using the `client_credentials` grant type:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/oauth/token \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "grant_type": "client_credentials",
  "client_id": "your-client-id",
  "client_secret": "your-client-secret"
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning the requested access token:

```javascript
{
    "access_token": "your-access-token",
    "token_type": "bearer",
    "expires_in": 7200,
    "scope": "market:all",
    "created_at": 123456789
}
```
{% endtab %}
{% endtabs %}

