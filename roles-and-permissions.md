---
description: How to set specific permitted actions for each resource
---

# Roles and permissions

Commerce Layer supports a granular access control system on a resource level. Each access token gets a specific set of permissions. The client and the [authorization flow](authentication/#authorization-flows) determine your permitted actions for each resource.

### Sales channel

**Sales channel** applications support `client_credentials`, `password` and `refresh_token` grant types. Given their limited permissions, they can be safely used in client-side applications.

#### Client credentials

**Sales channel** applications that authenticate through `client_credentials` get the following permissions.

{% hint style="danger" %}
For security reasons **sales channel** applications can read resource lists only for `skus`, `sku_options` and `prices`. Getting a list for all the other resources is not allowed. For example, a sales channel is authorized to get `/api/orders/xYZkjABcde` but not `/api/orders` endpoint.
{% endhint %}

|  | Create | Read | Update | Delete | Restrictions |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Addresses** | ✅ | ✅ | ✅ | ✅ | Single resource only. |
| **Customers** | ✅ |  |  |  |  |
| **Customer subscriptions** | ✅ | ✅ | ✅ | ✅ | Single resource only. |
| **Gift cards** | ✅ | ✅ | ✅ | ✅ | If "draft" \(single resource only\). |
| **Gift card recipients** | ✅ | ✅ | ✅ | ✅ | Single resource only. |
| **Orders** | ✅ | ✅ | ✅ |  | Can be read if "draft", "pending" or "placed" and updated if "draft" or "pending" \(single resource only\). |
| **Line items** | ✅ | ✅ | ✅ | ✅ | Can be read if  belonging to "draft", "pending" or "placed" orders and updated/deleted if belonging to "draft" or "pending" orders \(single resource only\). |
| **Line item options** | ✅ | ✅ | ✅ | ✅ | Can be read if  belonging line items associated with "draft", "pending" or "placed" orders and updated/deleted if belonging to line items associated with "draft" or "pending" orders \(single resource only\). |
| **Payment methods** |  | ✅ |  |  | Enabled payment methods associated with the market in scope. |
| **Payment sources** | ✅ | ✅ | ✅ | ✅ | Can be read if  belonging to "draft", "pending" or "placed" orders and updated/deleted if belonging to "draft" or "pending" orders \(single resource only\). |
| **Prices** |  | ✅ |  |  | Prices associated with the market price list. |
| **Returns** | ✅ | ✅ | ✅ |  | Can be created for orders associated with the market in scope and updated if in "draft" status \(single resource only\). |
| **Return Line Items** | ✅ | ✅ |  |  | Single resource only. |
| **Shipments** |  | ✅ | ✅ |  | Can be read if  belonging to "draft", "pending" or "placed" orders and updated if belonging to "draft" or "pending" orders \(single resource only\). |
| **Shipment line items** |  | ✅ |  |  | Can be read if  belonging to shipments associated with "draft", "pending" or "placed" orders \(single resource only\). |
| **Shipping methods** |  | ✅ |  |  | Enabled shipping methods associated with the market in scope. |
| **SKUs** |  | ✅ |  |  | SKUs with stock items in the market inventory model and a price in the market price list. |
| **SKU options** |  | ✅ |  |  | SKU options associated with the market in scope. |
| **SKU lists** | ✅ | ✅ | ✅ | ✅ | Single resource only. |
| **SKU list items** | ✅ | ✅ | ✅ | ✅ | Single resource only. |

#### Password

**Sales channel** applications can authenticate a customer through the `password` flow. The access tokens that they get include the sum of the client permissions plus the ones below.

|  | Create | Read | Update | Delete | Restrictions |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Customers** |  | ✅ | ✅ | ✅ | The customer must be the authenticated resource owner. |
| **Customer addresses** | ✅ | ✅ | ✅ | ✅ | The customer must be the authenticated resource owner. |
| **Customer payment sources** |  | ✅ | ✅ | ✅ | The customer must be the authenticated resource owner. |
| **Customer subscriptions** | ✅ | ✅ | ✅ | ✅ | The customer must be the authenticated resource owner. |
| **Line items** | ✅ | ✅ | ✅ | ✅ | The line items must belong to one of the customer's orders. |
| **Line item options** | ✅ | ✅ | ✅ | ✅ | The line item options must belong to one of the line items associated with one of the customer's orders. |
| **Orders** | ✅ | ✅ | ✅ |  | The customer must be the authenticated resource owner. |
| **Parcels** | ✅ |  |  |  | The parcels must belong to one of the customer's orders. |
| **Shipments** |  | ✅ | ✅ |  | The shipments must belong to one of the customer's orders. |

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

