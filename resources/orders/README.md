---
description: The order object and its fields
---

# Orders

Orders get created in a "draft" status and become "pending" when they have a customer and some line items.
Draft orders act as shopping carts. Pending orders can be recovered when abandoned.
When an order is placed, it can either get "approved" or "canceled".
An approved order becomes "fulfilled" when paid and shipped.
Canceling an order automatically voids its payment source's authorization.


### The order object

An **order** object is returned as part of the response body of each successful
[create](https://docs.commercelayer.io/resources/orders/create_order),
[list](https://docs.commercelayer.io/resources/orders/list_orders),
[retrieve](https://docs.commercelayer.io/resources/orders/retrieve_order),
or [update](https://docs.commercelayer.io/resources/orders/update_order) API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `orders` |
| **id** | `string` | The order unique identifier |
| links.**self** | `string` | The order endpoint URL |
| attributes.**number** | `integer` | Unique identified for the order (numeric) |
| attributes.**status** | `string` | The order status. One of 'draft' (default), 'pending', 'placed', 'approved', or 'cancelled' |
| attributes.**payment_status** | `string` | The order's payment status. One of 'unpaid' (default), 'authorized', 'paid', 'voided', or 'refunded' |
| attributes.**fulfillment_status** | `string` | The order's fulfillment status. One of 'unfulfilled' (default), 'in_progress', or 'fulfilled' |
| attributes.**guest** | `boolean` | Indicates if the order has been placed as guest. |
| attributes.**editable** | `boolean` | Indicates if the order can be edited. |
| attributes.**placeable** | `boolean` | Indicates if the order can be placed. |
| attributes.**customer_email** | `string` | The email address of the associated customer. When creating or updating an order, this is a shortcut to find or create the associated customer by email. |
| attributes.**customer_password** | `string` | The password of the associated customer. When creating or updating an order, this is a shortcut to sign up the associated customer. |
| attributes.**language_code** | `string` | The preferred language code (ISO 639-1) to be used when communicating with the customer. This can be useful when sending the order to 3rd party marketing tools and CRMs. If the language is supported, the hosted checkout will be localized accordingly. |
| attributes.**currency_code** | `string` | The international 3-letter currency code as defined by the ISO 4217 standard, automatically inherited from the order's market. |
| attributes.**tax_included** | `boolean` | Indicates if taxes are included in the order amounts, automatically inherited from the order's price list. |
| attributes.**tax_rate** | `float` | The tax rate for this order (if calculated). |
| attributes.**freight_taxable** | `boolean` | Indicates if taxes are applied to shipping costs. |
| attributes.**country_code** | `string` | The international 2-letter country code as defined by the ISO 3166-1 standard, automatically inherited from the order's shipping address. |
| attributes.**shipping_country_code_lock** | `string` | The country code that you want the shipping address to be locked to. This can be useful to make sure the shipping address belongs to a given shipping country, e.g. the one selected in a country selector page. |
| attributes.**coupon_code** | `string` | The coupon code to be used for the order. If valid, it triggers a promotion adding a discount line item to the order. |
| attributes.**subtotal_amount_cents** | `integer` | The sum of all the sku line items total amounts, in cents. |
| attributes.**subtotal_amount_float** | `float` | The sum of all the sku line items total amounts, float. |
| attributes.**formatted_subtotal_amount** | `string` | The sum of all the sku line items total amounts, formatted. |
| attributes.**shipping_amount_cents** | `integer` | The sum of all the shipping costs, in cents. |
| attributes.**shipping_amount_float** | `float` | The sum of all the shipping costs, float. |
| attributes.**formatted_shipping_amount** | `string` | The sum of all the shipping costs, formatted. |
| attributes.**payment_method_amount_cents** | `integer` | The sum of all the payment method costs, in cents. |
| attributes.**payment_method_amount_float** | `float` | The sum of all the payment method costs, float. |
| attributes.**formatted_payment_method_amount** | `string` | The sum of all the payment method costs, formatted. |
| attributes.**discount_amount_cents** | `integer` | The sum of all the discounts applied to the order, in cents (negative amount). |
| attributes.**discount_amount_float** | `float` | The sum of all the discounts applied to the order, float. |
| attributes.**formatted_discount_amount** | `string` | The sum of all the discounts applied to the order, formatted. |
| attributes.**total_tax_amount_cents** | `integer` | The sum of all the taxes applied to the order, in cents. |
| attributes.**total_tax_amount_float** | `float` | The sum of all the taxes applied to the order, float. |
| attributes.**formatted_total_tax_amount** | `string` | The sum of all the discounts applied to the order, formatted. |
| attributes.**subtotal_tax_amount_cents** | `integer` | The taxes applied to the order's subtotal, in cents. |
| attributes.**subtotal_tax_amount_float** | `float` | The taxes applied to the order's subtotal, float. |
| attributes.**formatted_subtotal_tax_amount** | `string` | The sum of all the discounts applied to the order, formatted. |
| attributes.**shipping_tax_amount_cents** | `integer` | The taxes applied to the order's shipping costs, in cents. |
| attributes.**shipping_tax_amount_float** | `float` | The taxes applied to the order's shipping costs, float. |
| attributes.**formatted_shipping_tax_amount** | `string` | The taxes applied to the order's shipping costs, formatted. |
| attributes.**payment_method_tax_amount_cents** | `integer` | The taxes applied to the order's payment method costs, in cents. |
| attributes.**payment_method_tax_amount_float** | `float` | The taxes applied to the order's payment method costs, float. |
| attributes.**formatted_payment_method_tax_amount** | `string` | The taxes applied to the order's payment method costs, formatted. |
| attributes.**discount_tax_amount_cents** | `integer` | The taxes applied to the order's discount, in cents (negative amount). |
| attributes.**discount_tax_amount_float** | `float` | The taxes applied to the order's discount, float. |
| attributes.**formatted_discount_tax_amount** | `string` | The taxes applied to the order's discount, formatted. |
| attributes.**total_amount_cents** | `integer` | The order's total amount, in cents. |
| attributes.**total_amount_float** | `float` | The order's total amount, float. |
| attributes.**formatted_total_amount** | `string` | The order's total amount, formatted. |
| attributes.**total_taxable_amount_cents** | `integer` | The order's total taxable amount, in cents (equal to total_amount_cents when prices don't include taxes). |
| attributes.**total_taxable_amount_float** | `float` | The order's total taxable amount, float. |
| attributes.**formatted_total_taxable_amount** | `string` | The order's total taxable amount, formatted. |
| attributes.**subtotal_taxable_amount_cents** | `integer` | The order's subtotal taxable amount, in cents (equal to subtotal_amount_cents when prices don't include taxes). |
| attributes.**subtotal_taxable_amount_float** | `float` | The order's subtotal taxable amount, float. |
| attributes.**formatted_subtotal_taxable_amount** | `string` | The order's subtotal taxable amount, formatted. |
| attributes.**shipping_taxable_amount_cents** | `integer` | The order's shipping taxable amount, in cents (equal to shipping_amount_cents when prices don't include taxes). |
| attributes.**shipping_taxable_amount_float** | `float` | The order's shipping taxable amount, float. |
| attributes.**formatted_shipping_taxable_amount** | `string` | The order's shipping taxable amount, formatted. |
| attributes.**payment_method_taxable_amount_cents** | `integer` | The order's payment method taxable amount, in cents (equal to payment_method_amount_cents when prices don't include taxes). |
| attributes.**payment_method_taxable_amount_float** | `float` | The order's payment method taxable amount, float. |
| attributes.**formatted_payment_method_taxable_amount** | `string` | The order's payment method taxable amount, formatted. |
| attributes.**discount_taxable_amount_cents** | `integer` | The order's discount taxable amount, in cents (equal to discount_amount_cents when prices don't include taxes). |
| attributes.**discount_taxable_amount_float** | `float` | The order's discount taxable amount, float. |
| attributes.**formatted_discount_taxable_amount** | `string` | The order's discount taxable amount, formatted. |
| attributes.**total_amount_with_taxes_cents** | `integer` | The order's total amount (when prices include taxes) or the order's total + taxes amount (when prices don't include taxes, e.g. US Markets or B2B) |
| attributes.**total_amount_with_taxes_float** | `float` | The order's total amount with taxes, float. |
| attributes.**formatted_total_amount_with_taxes** | `string` | The order's total amount with taxes, formatted. |
| attributes.**fees_amount_cents** | `integer` | The fees amount that is applied by Commerce Layer, in cents. |
| attributes.**fees_amount_float** | `float` | The fees amount that is applied by Commerce Layer, float. |
| attributes.**formatted_fees_amount** | `string` | The fees amount that is applied by Commerce Layer, formatted. |
| attributes.**skus_count** | `integer` | The total number of skus in the order's line items. This can be useful to display a preview of the customer shopping cart content. |
| attributes.**line_item_options_count** | `integer` | The total number of line item options. This can be useful to display a preview of the customer shopping cart content. |
| attributes.**shipments_count** | `integer` | The total number of shipments. This can be useful to manage the shipping method(s) selection during checkout. |
| attributes.**payment_source_details** | `object` | An object that contains the shareable details of the order's payment source. |
| attributes.**token** | `string` | A unique token that can be shared more securely instead of the order's id. |
| attributes.**cart_url** | `string` | The cart url on your site. If present, it will be used on our hosted checkout application. |
| attributes.**return_url** | `string` | The return url on your site. If present, it will be used on our hosted checkout application. |
| attributes.**terms_url** | `string` | The terms and conditions url on your site. If present, it will be used on our hosted checkout application. |
| attributes.**privacy_url** | `string` | The privacy polivy url on your site. If present, it will be used on our hosted checkout application. |
| attributes.**checkout_url** | `string` | The checkout url that was automatically generated for the order. Send the customers to this url to let them checkout the order securely on our hosted checkout application. |
| attributes.**_place** | `integer, value is '1'` | Send this attribute if you want to place the order. |
| attributes.**_cancel** | `integer, value is '1'` | Send this attribute if you want to cancel a placed order. The order's authorization will be automatically voided. |
| attributes.**_approve** | `integer, value is '1'` | Send this attribute if you want to approve a placed order. |
| attributes.**_capture** | `integer, value is '1'` | Send this attribute if you want to capture an approved order. |
| attributes.**_refund** | `integer, value is '1'` | Send this attribute if you want to refund a captured order. |
| attributes.**_update_taxes** | `integer, value is '1'` | Send this attribute if you want to calculate taxes for this order (a tax calculator must be associated to the order's market). |
| attributes.**_billing_address_clone_id** | `integer` | The id of the address that you want to clone to create the order's billing address. |
| attributes.**_shipping_address_clone_id** | `integer` | The id of the address that you want to clone to create the order's shipping address. |
| attributes.**_customer_payment_source_id** | `integer` | The id of the customer payment source (i.e. credit card) that you want to use as the order's payment source. |
| attributes.**_shipping_address_same_as_billing** | `integer, value is '1'` | Send this attribute if you want the shipping address to be cloned from the order's billing address. |
| attributes.**_billing_address_same_as_shipping** | `integer, value is '1'` | Send this attribute if you want the billing address to be cloned from the order's shipping address. |
| attributes.**_save_payment_source_to_customer_wallet** | `integer, value is '1'` | Send this attribute if you want the order's payment source to be saved in the customer's wallet as a customer payment source. |
| attributes.**_save_shipping_address_to_customer_address_book** | `integer, value is '1'` | Send this attribute if you want the order's shipping address to saved in the customer's address book as a customer address. |
| attributes.**_save_billing_address_to_customer_address_book** | `integer, value is '1'` | Send this attribute if you want the order's billing address to saved in the customer's address book as a customer address. |
| attributes.**_refresh** | `integer, value is '1'` | Send this attribute if you want to refresh an order. |
| attributes.**placed_at** | `datetime` | Time at which the order was placed. |
| attributes.**approved_at** | `datetime` | Time at which the order was approved. |
| attributes.**cancelled_at** | `datetime` | Time at which the order was cancelled. |
| attributes.**payment_updated_at** | `datetime` | Time at which the order's payment status was last updated. |
| attributes.**fulfillment_updated_at** | `datetime` | Time at which the order's fulfillment status was last updated. |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for integrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| relationships.**market** | `object` | The associated market. |
| relationships.**customer** | `object` | The associated customer. |
| relationships.**shipping_address** | `object` | The customer's shipping address. |
| relationships.**billing_address** | `object` | The customer's billing address. |
| relationships.**available_payment_methods** | `array` | The available payment methods for the shipment. Useful to present the customer with a list of choices during the checkout. Only enabled payment methods are included in the list. |
| relationships.**payment_method** | `object` | The associated payment method. |
| relationships.**payment_source** | `object` | The associated payment source (credit card or paypal payment). |
| relationships.**line_items** | `array` | The associated line items. |
| relationships.**shipments** | `array` | The associated shipments (automatically generated based on the inventory model). |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
