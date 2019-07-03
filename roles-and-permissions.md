---
description: How to set specific permitted actions for each resource
---

# Roles and permissions

Commerce Layer supports a granular access control system on a resource level. Each access token gets a specific set of permissions. The client and the [authorization flow](authentication/#authorization-flows) determine your permitted actions for each resource.

### Channel

**Channel** applications support `client_credentials`, `password` and `refresh_token` grant types. If public access is enabled, they can authenticate without the `client_secret`. In such cases, the access tokens that they get have limited permissions on sensitive data.

#### Client credentials

**Channel** applications that authenticate through `client_credentials` get the following permissions. The green icons ✅ show the ones that are granted with public access enabled.

|  | Create | Read | Update | Delete | Restrictions |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **SKUs** |  | ✅  |  |  | Skus with stock items in the market stock locations and a price in the market's price list. |
| **Prices** |  | ✅ |  |  | Prices associated to the market price list. |
| **Stock items** | \*\*\*\* | ✅ |  |  | Stock items associated to the market stock locations. |
| **Delivery lead times** | \*\*\*\* | ✅ |  |  | Delivery lead times associated to the market stock locations. |
| **Orders** | ✅ | ✅ | ☑  |  | Orders associated to the market scope. Can be read if "draft", "pending" or "placed" and updated if "draft" or "pending". Order lists are limited to one result. |
| **Line items** | ✅ | ✅ | ✅ | ✅ | Line items belonging to "draft" or "pending" orders, in the market scope. |
| **Addresses** | ☑  | ☑ | ☑ | ☑ |  |
| **Shipping methods** | \*\*\*\* | ✅ |  |  | Shipping methods associated to the market scope. |
| **Shipments** |  | ☑ | ☑ |  | Shipments associated to "draft" or "pending" orders, in the market scope. |
| **Payment methods** | \*\*\*\* | ✅ |  |  | Payment methods associated to the market scope. |
| **Credit cards** | ☑ | ☑ | ☑ |  | Credit cards associated to "draft" or "pending" orders, in the market scope. |
| **Paypal payments** | ☑ | ☑ | ☑ |  | Paypal payments associated to "draft" or "pending" orders, in the market scope. |
| **Customers** | ✅ |  |  |  |  |
| **Customer subscriptions** | ✅ |  |  |  |  |
| **Customer password resets** | ☑ | ☑ | ☑ | ☑ |  |

#### Password

**Channel** applications can authenticate a customer through the `password` flow. The access tokens that they get include the sum of the client permissions plus the ones below.

|  | Create | Read | Update | Delete | Restrictions |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Customers** |  | ✅ | ✅ | ✅ | The customer must be the authenticated resource owner. |
| **Customer addresses** | ✅ | ✅ | ✅ | ✅ | The customer must be the authenticated resource owner. |
| **Customer subscriptions** | ✅ | ✅ | ✅ | ✅ | The customer must be the authenticated resource owner. |
| **Orders** | ✅ | ✅ | ✅ |  | The customer must be the authenticated resource owner. |
| **Parcels** | ✅ |  |  |  | The parcels must belong to one of the customer's orders. |

#### Refresh token

An access token obtained through a `refresh_token` inherit the same set of permissions of the one that expired.

### Integration

**Integration** applications support the `client_credentials` grant type. The access tokens that they get include the set of permissions of their role.

### Webapp

**Webapp** applications support `authorization_code` and `refresh_token` grant types. They don't bring any grants to the access tokens, and get the set of permissions of to the authenticated user's role. Access tokens obtained through a `refresh_token` inherit the same set of permissions of the one that expired.

### Other application types

Other application types \(such as [Zapier](https://zapier.com/), [Contentful](https://www.contentful.com/), [DatoCMS](https://www.datocms.com/) etc.\) have more straightforward authorization rules and get the right amount of permissions that are required by the relevant tool.

{% hint style="warning" %}
Commerce Layer Zapier app is currently private. Feel free to [accept this invitation](https://zapier.com/developer/public-invite/1418/4068b989bdb97d852a4e199b1d1adf46/) and start building your zaps!
{% endhint %}

