---
description: The complete list of supported events for each resource
---

# Real-time webhooks

Commerce Layer provides a [webhook](https://en.wikipedia.org/wiki/Webhook) mechanism to react to specific events in real-time. 

Each time a subscribed event occurs, we trigger a `POST` request to the endpoint that you specified in the `callback_url` field. The request contains a JSON payload in the same format that you get when fetching the same resource through the REST API. 

{% page-ref page="fetching-resources.md" %}

For each resource, you can also configure the related resources that should be included in the request body. The relationships will be set as the resource `include` query parameter.

{% page-ref page="including-associations.md" %}

When you create a new webhook, a **shared secret** is generated. It will be used each time the webhook is fired to sign the payload. The related signature will be stored in the **X-CommerceLayer-Signature** header so that you can verify the callback authenticity and consider it reliable.

{% page-ref page="callbacks-security.md" %}

### Supported events

You can find here below the complete list of all the topics `{{resource}}.{{event}}` you can monitor:

| Topic | Trigger |
| :--- | :--- |
| authorizations.**create** | A new authorization transaction is created |
| captures.**create** | A new capture transaction is created |
| customer\_addresses.**create** | A new customer address is created |
| customer\_addresses.**destroy** | An existing `customer_addresses` object is deleted |
| customer\_password\_resets.**create** | A customer password reset process is initiated |
| customer\_password\_resets.**destroy** | An existing `customer_password_resets` object is deleted |
| customer\_password\_resets.**reset\_password** | A customer password is reset |
| customer\_subscriptions.**create** | A new customer subscription is created |
| customer\_subscriptions.**destroy** | An existing `customer_subscriptions` object is deleted |
| customers.**create** | A new customer is created |
| customers.**acquired**  | An existing customer status is set to `acquired` |
| customers.**repeat** | An existing customer status is set to `repeat` |
| customers.**create\_password**  | A new password for a customer is created |
| customers.**metadata\_update** | An existing customer metatdata are updated |
| customers.**destroy** | An existing `customers` object is deleted |
| external\_promotions.**create** | An external promotion is created |
| external\_promotions.**destroy** | An existing `external_promotions` object is deleted |
| fixed\_amount\_promotions.**create** | A fixed amount promotion is created |
| fixed\_amount\_promotions.**destroy** | An existing `fixed_amount_promotions` object is deleted |
| free\_shipping\_promotions.**create** | A free shipping promotion is created |
| free\_shipping\_promotions.**destroy** | An existing `free_shipping_promotions` object is deleted |
| gift\_cards.**create** | A new gift card is created |
| gift\_cards.**purchase** | An existing gift card is purchased |
| gift\_cards.**activate** | An existing gift card status is set to `active` |
| gift\_cards.**deactivate** | An active gift card status is set to `inactive` |
| gift\_cards.**redeem** | An existing gift card status is set to `redeemed` |
| gift\_cards.**destroy** | An existing `gift_cards` object is deleted |
| imports.**create** | A new import is created |
| imports.**start**  | An existing import status is set to `started` |
| imports.**complete**  | An existing import status is set to `completed` |
| imports.**interrupt** | An existing import is interrupted |
| imports.**destroy** | An existing `imports` object is deleted |
| in\_stock\_subscriptions.**create** | A new in-stock subscription is created |
| in\_stock\_subscriptions.**activate** | An existing in-stock subscription status is set to `active` |
| in\_stock\_subscriptions.**deactivate** | An existing in-stock subscription status is set to `inactive` |
| in\_stock\_subscriptions.**notify** | An existing in-stock subscription status is set to `notified` |
| in\_stock\_subscriptions.**destroy** | An existing `in_stock_subscriptions` object is deleted |
| orders.**create** | A new order is created |
| orders.**draft**  | An existing order status is set to `draft` |
| orders.**pending** | An existing order status is set to `pending` |
| orders.**place** | An existing order status is set to `placed` |
| orders.**approve** | An existing order status is set to `approved` |
| orders.**cancel** | An existing order status is set to `cancelled` |
| orders.**authorize** | An existing order payment status is set to `authorized` |
| orders.**void**  | An existing order payment status is set to `voided` |
| orders.**pay** | An existing order payment status is set to `paid` |
| orders.**refund** | An existing order payment status is set to `refunded` |
| orders.**start\_fulfilling**  | An existing order fulfillment status is set to `in_progress` |
| orders.**fulfill** | An existing order fulfillment status is set to `fulfilled` |
| orders.**rebuild\_shipments** | An existing order's shipments are rebuilt |
| orders.**destroy** | An existing `orders` object is deleted |
| parcels.**create**  | A new parcel is created |
| parcels.**destroy** | An existing orders `parcels` object is deleted |
| percentage\_discount\_promotions.**create** | A new percentage discount promotion is created |
| percentage\_discount\_promotions.**destroy** | An existing `percentage_discount_promotion` object is deleted |
| refunds.**create** | A new refund is created |
| returns.**create** | A new return is created |
| returns.**request** | An existing return status is set to `requested` |
| returns.**pending** | An existing return status is set to `pending` |
| returns.**approve** | An existing return status is set to `approved` |
| returns.**reject** | An existing return status is set to `rejected` |
| returns.**ship** | An existing return status is set to `shipped` |
| returns.**receive** | An existing return status is set to `received` |
| returns.**restock** | An existing return's line items are restocked |
| returns.**destroy** | An existing `returns` object is deleted |
| shipments.**create** | A new shipment is created |
| shipments.**upcoming**  | An existing shipment status is set to `upcoming` |
| shipments.**cancel** | An existing shipment status is set to `cancelled` |
| shipments.**on\_hold** | An existing shipment status is set to `on_hold` |
| shipments.**picking** | An existing shipment status is set to `picking` |
| shipments.**packing**  | An existing shipment status is set to `packing` |
| shipments.**ready\_to\_ship** | An existing shipment status is set to `ready_to_ship` |
| shipments.**ship** | An existing shipment status is set to `shipped` |
| shipments.**destroy** | An existing `shipments` object is deleted |
| stock\_transfers.**create** | A new stock transfer is created |
| stock\_transfers.**upcoming** | An existing stock transfer status is set to `upcoming` |
| stock\_transfers.**picking** | An existing stock transfer status is set to `picking` |
| stock\_transfers.**in\_transit** | An existing stock transfer status is set to `in_transit` |
| stock\_transfers.**complete** | An existing stock transfer status is set to `completed` |
| stock\_transfers.**cancel** | An existing stock transfer status is set to `cancelled` |
| stock\_transfers.**destroy** | An existing `stock_transfers` object is deleted |
| voids.**create** | A new void transaction is created |

### Responding to webhook callbacks

The endpoint listening for webhooks has **5 seconds** to respond with a **`2xx`** \(usually `200` \) response code,  acknowledging a successful delivery. If the request times out or gets a response with a status code other than `2xx`, it is considered failed.

### Handling webhook failures

If a webhook fails \(whatever the reason\) Commerce Layer tries to fire it again up to **10 times**. After **30 consecutive failures** \(retry failures included\) no further calls to the related endpoint are made and the webhook has to be reset.

{% hint style="info" %}
To let you properly handle this scenario and inspect the reasons for the failure,  after **5** consecutive non-successful attempts a communication is sent to the owner of the organization.
{% endhint %}

