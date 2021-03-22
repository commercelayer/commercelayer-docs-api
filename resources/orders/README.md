---
description: The order object and its fields
---

# Orders

Orders get created in a "draft" status and become "pending" when they have a customer and some line items. Draft orders act as shopping carts. Pending orders can be recovered when abandoned. When an order is placed, it can either get "approved" or "cancelled". An approved order becomes "fulfilled" when paid and shipped. Canceling an order automatically voids its payment source's authorization.

## The order object

An **order** object is returned as part of the response body of each successful list, retrieve, create or update API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `orders` |
| **id** | `string` | The order unique identifier |
| links.**self** | `string` | The order endpoint URL |
| attributes.**number** | `integer` | Unique identifier for the order \(numeric\) |
| attributes.**status** | `string` | The order status. One of 'draft' \(default\), 'pending', 'placed', 'approved', or 'cancelled' |
| attributes.**payment\_status** | `string` | The order's payment status. One of 'unpaid' \(default\), 'authorized', 'paid', 'voided', or 'refunded' |
| attributes.**fulfillment\_status** | `string` | The order's fulfillment status. One of 'unfulfilled' \(default\), 'in\_progress', or 'fulfilled' |
| attributes.**guest** | `boolean` | Indicates if the order has been placed as guest. |
| attributes.**editable** | `boolean` | Indicates if the order can be edited. |
| attributes.**placeable** | `boolean` | Indicates if the order can be placed. |
| attributes.**customer\_email** | `string` | The email address of the associated customer. When creating or updating an order, this is a shortcut to find or create the associated customer by email. |
| attributes.**customer\_password** | `string` | The password of the associated customer. When creating or updating an order, this is a shortcut to sign up the associated customer. |
| attributes.**language\_code** | `string` | The preferred language code \(ISO 639-1\) to be used when communicating with the customer. This can be useful when sending the order to 3rd party marketing tools and CRMs. If the language is supported, the hosted checkout will be localized accordingly. |
| attributes.**currency\_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard, automatically inherited from the order's market. |
| attributes.**tax\_included** | `boolean` | Indicates if taxes are included in the order amounts, automatically inherited from the order's price list. |
| attributes.**tax\_rate** | `float` | The tax rate for this order \(if calculated\). |
| attributes.**freight\_taxable** | `boolean` | Indicates if taxes are applied to shipping costs. |
| attributes.**requires\_billing\_info** | `boolean` | Indicates if the billing address associated to this order requires billing info to be present. |
| attributes.**country\_code** | `string` | The international 2-letter country code as defined by the ISO 3166-1 standard, automatically inherited from the order's shipping address. |
| attributes.**shipping\_country\_code\_lock** | `string` | The country code that you want the shipping address to be locked to. This can be useful to make sure the shipping address belongs to a given shipping country, e.g. the one selected in a country selector page. |
| attributes.**coupon\_code** | `string` | The coupon code to be used for the order. If valid, it triggers a promotion adding a discount line item to the order. |
| attributes.**gift\_card\_code** | `string` | The gift card code \(at least the first 8 characters\) to be used for the order. If valid, it uses the gift card balance to pay for the order. |
| attributes.**gift\_card\_or\_coupon\_code** | `string` | The gift card or coupon code \(at least the first 8 characters\) to be used for the order. If a gift card mathes, it uses the gift card balance to pay for the order. Otherwise it tries to find a valid coupon code and applies the associated discount. |
| attributes.**subtotal\_amount\_cents** | `integer` | The sum of all the sku line items total amounts, in cents. |
| attributes.**subtotal\_amount\_float** | `float` | The sum of all the sku line items total amounts, float. |
| attributes.**formatted\_subtotal\_amount** | `string` | The sum of all the sku line items total amounts, formatted. |
| attributes.**shipping\_amount\_cents** | `integer` | The sum of all the shipping costs, in cents. |
| attributes.**shipping\_amount\_float** | `float` | The sum of all the shipping costs, float. |
| attributes.**formatted\_shipping\_amount** | `string` | The sum of all the shipping costs, formatted. |
| attributes.**payment\_method\_amount\_cents** | `integer` | The sum of all the payment method costs, in cents. |
| attributes.**payment\_method\_amount\_float** | `float` | The sum of all the payment method costs, float. |
| attributes.**formatted\_payment\_method\_amount** | `string` | The sum of all the payment method costs, formatted. |
| attributes.**discount\_amount\_cents** | `integer` | The sum of all the discounts applied to the order, in cents \(negative amount\). |
| attributes.**discount\_amount\_float** | `float` | The sum of all the discounts applied to the order, float. |
| attributes.**formatted\_discount\_amount** | `string` | The sum of all the discounts applied to the order, formatted. |
| attributes.**adjustment\_amount\_cents** | `integer` | The sum of all the adjustments applied to the order, in cents. |
| attributes.**adjustment\_amount\_float** | `float` | The sum of all the adjustments applied to the order, float. |
| attributes.**formatted\_adjustment\_amount** | `string` | The sum of all the adjustments applied to the order, formatted. |
| attributes.**gift\_card\_amount\_cents** | `integer` | The sum of all the gift\_cards applied to the order, in cents. |
| attributes.**gift\_card\_amount\_float** | `float` | The sum of all the gift\_cards applied to the order, float. |
| attributes.**formatted\_gift\_card\_amount** | `string` | The sum of all the gift\_cards applied to the order, formatted. |
| attributes.**total\_tax\_amount\_cents** | `integer` | The sum of all the taxes applied to the order, in cents. |
| attributes.**total\_tax\_amount\_float** | `float` | The sum of all the taxes applied to the order, float. |
| attributes.**formatted\_total\_tax\_amount** | `string` | The sum of all the taxes applied to the order, formatted. |
| attributes.**subtotal\_tax\_amount\_cents** | `integer` | The taxes applied to the order's subtotal, in cents. |
| attributes.**subtotal\_tax\_amount\_float** | `float` | The taxes applied to the order's subtotal, float. |
| attributes.**formatted\_subtotal\_tax\_amount** | `string` | The taxes applied to the order's subtotal, formatted. |
| attributes.**shipping\_tax\_amount\_cents** | `integer` | The taxes applied to the order's shipping costs, in cents. |
| attributes.**shipping\_tax\_amount\_float** | `float` | The taxes applied to the order's shipping costs, float. |
| attributes.**formatted\_shipping\_tax\_amount** | `string` | The taxes applied to the order's shipping costs, formatted. |
| attributes.**payment\_method\_tax\_amount\_cents** | `integer` | The taxes applied to the order's payment method costs, in cents. |
| attributes.**payment\_method\_tax\_amount\_float** | `float` | The taxes applied to the order's payment method costs, float. |
| attributes.**formatted\_payment\_method\_tax\_amount** | `string` | The taxes applied to the order's payment method costs, formatted. |
| attributes.**adjustment\_tax\_amount\_cents** | `integer` | The taxes applied to the order adjustments, in cents. |
| attributes.**adjustment\_tax\_amount\_float** | `float` | The taxes applied to the order adjustments, float. |
| attributes.**formatted\_adjustment\_tax\_amount** | `string` | The taxes applied to the order adjustments, formatted. |
| attributes.**total\_amount\_cents** | `integer` | The order's total amount, in cents. |
| attributes.**total\_amount\_float** | `float` | The order's total amount, float. |
| attributes.**formatted\_total\_amount** | `string` | The order's total amount, formatted. |
| attributes.**total\_taxable\_amount\_cents** | `integer` | The order's total taxable amount, in cents \(equal to total\_amount\_cents when prices don't include taxes\). |
| attributes.**total\_taxable\_amount\_float** | `float` | The order's total taxable amount, float. |
| attributes.**formatted\_total\_taxable\_amount** | `string` | The order's total taxable amount, formatted. |
| attributes.**subtotal\_taxable\_amount\_cents** | `integer` | The order's subtotal taxable amount, in cents \(equal to subtotal\_amount\_cents when prices don't include taxes\). |
| attributes.**subtotal\_taxable\_amount\_float** | `float` | The order's subtotal taxable amount, float. |
| attributes.**formatted\_subtotal\_taxable\_amount** | `string` | The order's subtotal taxable amount, formatted. |
| attributes.**shipping\_taxable\_amount\_cents** | `integer` | The order's shipping taxable amount, in cents \(equal to shipping\_amount\_cents when prices don't include taxes\). |
| attributes.**shipping\_taxable\_amount\_float** | `float` | The order's shipping taxable amount, float. |
| attributes.**formatted\_shipping\_taxable\_amount** | `string` | The order's shipping taxable amount, formatted. |
| attributes.**payment\_method\_taxable\_amount\_cents** | `integer` | The order's payment method taxable amount, in cents \(equal to payment\_method\_amount\_cents when prices don't include taxes\). |
| attributes.**payment\_method\_taxable\_amount\_float** | `float` | The order's payment method taxable amount, float. |
| attributes.**formatted\_payment\_method\_taxable\_amount** | `string` | The order's payment method taxable amount, formatted. |
| attributes.**adjustment\_taxable\_amount\_cents** | `integer` | The order's adjustment taxable amount, in cents \(equal to discount\_adjustment\_cents when prices don't include taxes\). |
| attributes.**adjustment\_taxable\_amount\_float** | `float` | The order's adjustment taxable amount, float. |
| attributes.**formatted\_adjustment\_taxable\_amount** | `string` | The order's adjustment taxable amount, formatted. |
| attributes.**total\_amount\_with\_taxes\_cents** | `integer` | The order's total amount \(when prices include taxes\) or the order's total + taxes amount \(when prices don't include taxes, e.g. US Markets or B2B\) |
| attributes.**total\_amount\_with\_taxes\_float** | `float` | The order's total amount with taxes, float. |
| attributes.**formatted\_total\_amount\_with\_taxes** | `string` | The order's total amount with taxes, formatted. |
| attributes.**fees\_amount\_cents** | `integer` | The fees amount that is applied by Commerce Layer, in cents. |
| attributes.**fees\_amount\_float** | `float` | The fees amount that is applied by Commerce Layer, float. |
| attributes.**formatted\_fees\_amount** | `string` | The fees amount that is applied by Commerce Layer, formatted. |
| attributes.**duty\_amount\_cents** | `integer` | The duty amount that is calculated by external services, in cents. |
| attributes.**duty\_amount\_float** | `float` | The duty amount that is calculated by external services, float. |
| attributes.**formatted\_duty\_amount** | `string` | The duty amount that is calculated by external services, formatted. |
| attributes.**skus\_count** | `integer` | The total number of skus in the order's line items. This can be useful to display a preview of the customer shopping cart content. |
| attributes.**line\_item\_options\_count** | `integer` | The total number of line item options. This can be useful to display a preview of the customer shopping cart content. |
| attributes.**shipments\_count** | `integer` | The total number of shipments. This can be useful to manage the shipping method\(s\) selection during checkout. |
| attributes.**payment\_source\_details** | `object` | An object that contains the shareable details of the order's payment source. |
| attributes.**token** | `string` | A unique token that can be shared more securely instead of the order's id. |
| attributes.**cart\_url** | `string` | The cart url on your site. If present, it will be used on our hosted checkout application. |
| attributes.**return\_url** | `string` | The return url on your site. If present, it will be used on our hosted checkout application. |
| attributes.**terms\_url** | `string` | The terms and conditions url on your site. If present, it will be used on our hosted checkout application. |
| attributes.**privacy\_url** | `string` | The privacy polivy url on your site. If present, it will be used on our hosted checkout application. |
| attributes.**checkout\_url** | `string` | The checkout url that was automatically generated for the order. Send the customers to this url to let them checkout the order securely on our hosted checkout application. |
| attributes.**\_archive** | `boolean, value is 'true'` | Send this attribute if you want to archive the order. |
| attributes.**\_unarchive** | `boolean, value is 'true'` | Send this attribute if you want to unarchive the order. |
| attributes.**\_place** | `boolean, value is 'true'` | Send this attribute if you want to place the order. |
| attributes.**\_cancel** | `boolean, value is 'true'` | Send this attribute if you want to cancel a placed order. The order's authorization will be automatically voided. |
| attributes.**\_approve** | `boolean, value is 'true'` | Send this attribute if you want to approve a placed order. |
| attributes.**\_approve\_and\_capture** | `boolean, value is 'true'` | Send this attribute if you want to approve and capture a placed order. |
| attributes.**\_authorize** | `boolean, value is 'true'` | Send this attribute if you want to authorize the order's payment source. |
| attributes.**\_authorization\_amount\_cents** | `integer` | The authorization amount, in cents. |
| attributes.**\_capture** | `boolean, value is 'true'` | Send this attribute if you want to capture an approved order. |
| attributes.**\_refund** | `boolean, value is 'true'` | Send this attribute if you want to refund a captured order. |
| attributes.**\_update\_taxes** | `boolean, value is 'true'` | Send this attribute if you want to force tax calculation for this order \(a tax calculator must be associated to the order's market\). |
| attributes.**\_billing\_address\_clone\_id** | `string` | The id of the address that you want to clone to create the order's billing address. |
| attributes.**\_shipping\_address\_clone\_id** | `string` | The id of the address that you want to clone to create the order's shipping address. |
| attributes.**\_customer\_payment\_source\_id** | `string` | The id of the customer payment source \(i.e. credit card\) that you want to use as the order's payment source. |
| attributes.**\_shipping\_address\_same\_as\_billing** | `boolean, value is 'true'` | Send this attribute if you want the shipping address to be cloned from the order's billing address. |
| attributes.**\_billing\_address\_same\_as\_shipping** | `boolean, value is 'true'` | Send this attribute if you want the billing address to be cloned from the order's shipping address. |
| attributes.**\_save\_payment\_source\_to\_customer\_wallet** | `boolean, value is 'true'` | Send this attribute if you want the order's payment source to be saved in the customer's wallet as a customer payment source. |
| attributes.**\_save\_shipping\_address\_to\_customer\_address\_book** | `boolean, value is 'true'` | Send this attribute if you want the order's shipping address to saved in the customer's address book as a customer address. |
| attributes.**\_save\_billing\_address\_to\_customer\_address\_book** | `boolean, value is 'true'` | Send this attribute if you want the order's billing address to saved in the customer's address book as a customer address. |
| attributes.**\_refresh** | `boolean, value is 'true'` | Send this attribute if you want to refresh an order. |
| attributes.**placed\_at** | `datetime` | Time at which the order was placed. |
| attributes.**approved\_at** | `datetime` | Time at which the order was approved. |
| attributes.**cancelled\_at** | `datetime` | Time at which the order was cancelled. |
| attributes.**payment\_updated\_at** | `datetime` | Time at which the order's payment status was last updated. |
| attributes.**fulfillment\_updated\_at** | `datetime` | Time at which the order's fulfillment status was last updated. |
| attributes.**archived\_at** | `datetime` | Time at which the resource has been archived. |
| attributes.**expires\_at** | `datetime` | Time at which an order is marked for cleanup. Any order will start with a default expire time of 2 months. Expiration is reset once a line item is added to the order. |
| attributes.**created\_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated\_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add any external identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool, a CRM, or whatever. |
| attributes.**reference\_origin** | `string` | Any identifier of the third party system that defines the reference code |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**market** | `object` | The associated market. |
| relationships.**customer** | `object` | The associated customer. |
| relationships.**shipping\_address** | `object` | The customer's shipping address. |
| relationships.**billing\_address** | `object` | The customer's billing address. |
| relationships.**available\_payment\_methods** | `array` | The available payment methods for the shipment. Useful to present the customer with a list of choices during the checkout. Only enabled payment methods are included in the list. |
| relationships.**payment\_method** | `object` | The associated payment method. |
| relationships.**payment\_source** | `object` | The associated payment source \(one stripe payment, braintree payment, adyen payment, paypal payment, or wire transfer\). |
| relationships.**line\_items** | `array` | The associated line items. |
| relationships.**shipments** | `array` | The associated shipments \(automatically generated based on the inventory model\). |
| relationships.**transactions** | `array` | The associated transactions. |
| relationships.**authorizations** | `array` | The associated authorizations. |
| relationships.**captures** | `array` | The associated captures. |
| relationships.**voids** | `array` | The associated voids. |
| relationships.**refunds** | `array` | The associated refunds. |
| relationships.**attachments** | `array` | The associated attachments. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |

