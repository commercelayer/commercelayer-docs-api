---
description: 'How to get your access token, based on OAuth 2.0 grants'
---

# Authentication

All API requests must be authenticated. To get authorized, you must include a valid access token in the **Authorization** header:

```http
Authorization: Bearer your-access-token
```

### Authorization grant flows

To get an access token, you need to execute an authorization flow by using a valid application as the client. 

The authorization flow depends on the [grant type](https://oauth.net/2/grant-types/) as described in the table below:

| Grant type | Sales channel | Integration | Webapp |
| :--- | :--- | :--- | :--- |
| **Client credentials** | **✅** | **✅** |  |
| **Password** | **✅** |  |  |
| **Refresh token** | **✅** |  | **✅** |
| **Authorization code** | \*\*\*\* |  | **✅** |

{% hint style="warning" %}
For security reasons, access tokens expire after **2 hours**. Refresh tokens expire after **2 weeks**.
{% endhint %}

### Authorization scopes

For each of the above authorization flows you can restrict the scope to a specific market and/or stock location.

{% hint style="info" %}
The access token scope is a string composed by `"{{resource_name}}:{{resource_number}}"`, where `resource_number` is the **number** — not the ID — of the market or stock location you want to put in scope.
{% endhint %}

#### Putting a market in scope

By including a market scope in the access token request — `market:1234` — all the resources \(e.g. SKUs, prices, stock items\) that you fetch are automatically filtered.

```http
{
  "grant_type": "authorization-grant",
  "client_id": "your-client-id",
  ...,
  "scope": "market:1234"
}
```

{% hint style="warning" %}
**Sales channel** applications require a market in scope when requesting their access token to perform the [permitted CRUD actions](../roles-and-permissions.md#sales-channel).
{% endhint %}

#### Putting a stock location in scope

By including a stock location scope in the access token request — `stock_location:4567` — the stock is restricted to the SKUs available in that specific stock location.

```http
{
  "grant_type": "authorization-grant",
  "client_id": "your-client-id",
  ...,
  "scope": "market:1234 stock_location:4567"
}
```

{% hint style="warning" %}
When putting a stock location in scope, adding the associated market in the access token request is **mandatory**. If the market scope is missing or the stock location doesn't belong to the market in scope the API responds with a `400 Bad Request` error code.
{% endhint %}

