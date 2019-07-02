---
description: How to create An order via API
---

# Create An order

To create a new order, send a `POST` request to the `/api/orders` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain.commercelayer.io**/api/orders**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**number** | `integer` |  |
| attributes.**status** | `string` |  |
| attributes.**payment_status** | `string` |  |
| attributes.**fulfillment_status** | `string` |  |
| attributes.**guest** | `boolean` | optional |
| attributes.**editable** | `boolean` |  |
| attributes.**placeable** | `boolean` |  |
| attributes.**customer_email** | `string` | optional |
| attributes.**customer_password** | `string` | optional |
| attributes.**language_code** | `string` | optional, default is 'en' |
| attributes.**currency_code** | `string` |  |
| attributes.**tax_included** | `boolean` |  |
| attributes.**tax_rate** | `float` |  |
| attributes.**freight_taxable** | `boolean` |  |
| attributes.**country_code** | `string` |  |
| attributes.**shipping_country_code_lock** | `string` | optional |
| attributes.**coupon_code** | `string` | optional |
| attributes.**subtotal_amount_cents** | `integer` |  |
| attributes.**subtotal_amount_float** | `float` |  |
| attributes.**formatted_subtotal_amount** | `string` |  |
| attributes.**shipping_amount_cents** | `integer` |  |
| attributes.**shipping_amount_float** | `float` |  |
| attributes.**formatted_shipping_amount** | `string` |  |
| attributes.**payment_method_amount_cents** | `integer` |  |
| attributes.**payment_method_amount_float** | `float` |  |
| attributes.**formatted_payment_method_amount** | `string` |  |
| attributes.**discount_amount_cents** | `integer` |  |
| attributes.**discount_amount_float** | `float` |  |
| attributes.**formatted_discount_amount** | `string` |  |
| attributes.**total_tax_amount_cents** | `integer` |  |
| attributes.**total_tax_amount_float** | `float` |  |
| attributes.**formatted_total_tax_amount** | `string` |  |
| attributes.**subtotal_tax_amount_cents** | `integer` |  |
| attributes.**subtotal_tax_amount_float** | `float` |  |
| attributes.**formatted_subtotal_tax_amount** | `string` |  |
| attributes.**shipping_tax_amount_cents** | `integer` |  |
| attributes.**shipping_tax_amount_float** | `float` |  |
| attributes.**formatted_shipping_tax_amount** | `string` |  |
| attributes.**payment_method_tax_amount_cents** | `integer` |  |
| attributes.**payment_method_tax_amount_float** | `float` |  |
| attributes.**formatted_payment_method_tax_amount** | `string` |  |
| attributes.**discount_tax_amount_cents** | `integer` |  |
| attributes.**discount_tax_amount_float** | `float` |  |
| attributes.**formatted_discount_tax_amount** | `string` |  |
| attributes.**total_amount_cents** | `integer` |  |
| attributes.**total_amount_float** | `float` |  |
| attributes.**formatted_total_amount** | `string` |  |
| attributes.**total_taxable_amount_cents** | `integer` |  |
| attributes.**total_taxable_amount_float** | `float` |  |
| attributes.**formatted_total_taxable_amount** | `string` |  |
| attributes.**subtotal_taxable_amount_cents** | `integer` |  |
| attributes.**subtotal_taxable_amount_float** | `float` |  |
| attributes.**formatted_subtotal_taxable_amount** | `string` |  |
| attributes.**shipping_taxable_amount_cents** | `integer` |  |
| attributes.**shipping_taxable_amount_float** | `float` |  |
| attributes.**formatted_shipping_taxable_amount** | `string` |  |
| attributes.**payment_method_taxable_amount_cents** | `integer` |  |
| attributes.**payment_method_taxable_amount_float** | `float` |  |
| attributes.**formatted_payment_method_taxable_amount** | `string` |  |
| attributes.**discount_taxable_amount_cents** | `integer` |  |
| attributes.**discount_taxable_amount_float** | `float` |  |
| attributes.**formatted_discount_taxable_amount** | `string` |  |
| attributes.**total_amount_with_taxes_cents** | `integer` |  |
| attributes.**total_amount_with_taxes_float** | `float` |  |
| attributes.**formatted_total_amount_with_taxes** | `string` |  |
| attributes.**fees_amount_cents** | `integer` |  |
| attributes.**fees_amount_float** | `float` |  |
| attributes.**formatted_fees_amount** | `string` |  |
| attributes.**skus_count** | `integer` |  |
| attributes.**line_item_options_count** | `integer` |  |
| attributes.**shipments_count** | `integer` |  |
| attributes.**payment_source_details** | `object` |  |
| attributes.**token** | `string` |  |
| attributes.**cart_url** | `string` | optional |
| attributes.**return_url** | `string` | optional |
| attributes.**terms_url** | `string` | optional |
| attributes.**privacy_url** | `string` | optional |
| attributes.**checkout_url** | `string` |  |
| attributes.**_place** | `integer, value is '1'` |  |
| attributes.**_cancel** | `integer, value is '1'` |  |
| attributes.**_approve** | `integer, value is '1'` |  |
| attributes.**_capture** | `integer, value is '1'` |  |
| attributes.**_refund** | `integer, value is '1'` |  |
| attributes.**_update_taxes** | `integer, value is '1'` |  |
| attributes.**_billing_address_clone_id** | `integer` |  |
| attributes.**_shipping_address_clone_id** | `integer` |  |
| attributes.**_customer_payment_source_id** | `integer` | optional |
| attributes.**_shipping_address_same_as_billing** | `integer, value is '1'` | optional |
| attributes.**_billing_address_same_as_shipping** | `integer, value is '1'` | optional |
| attributes.**_save_payment_source_to_customer_wallet** | `integer, value is '1'` | optional |
| attributes.**_save_shipping_address_to_customer_address_book** | `integer, value is '1'` | optional |
| attributes.**_save_billing_address_to_customer_address_book** | `integer, value is '1'` | optional |
| attributes.**_refresh** | `integer, value is '1'` | optional |
| attributes.**placed_at** | `datetime` |  |
| attributes.**approved_at** | `datetime` |  |
| attributes.**cancelled_at** | `datetime` |  |
| attributes.**payment_updated_at** | `datetime` |  |
| attributes.**fulfillment_updated_at** | `datetime` |  |
| attributes.**id** | `string` | required |
| attributes.**created_at** | `datetime` | required |
| attributes.**updated_at** | `datetime` | required |
| attributes.**reference** | `string` | optional |
| attributes.**metadata** | `object` | optional |
| relationships.**market** | `has_one` | required |
| relationships.**customer** | `has_one` | optional |
| relationships.**shipping_address** | `has_one` | optional |
| relationships.**billing_address** | `has_one` | optional |
| relationships.**available_payment_methods** | `has_many` |  |
| relationships.**payment_method** | `has_one` | optional |
| relationships.**payment_source** | `has_one` | optional |
| relationships.**line_items** | `has_many` |  |
| relationships.**shipments** | `has_many` |  |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new order:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/orders \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "orders",
    "attributes": {
    },
    "relationships": {
      "market": {
        "data": {
          "type": "markets",
          "id": "zxcVBnMASd"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `order` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "orders",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde"
    },
    "attributes": {
        "number": "1234"
        "status": "draft"
        "payment_status": "unpaid"
        "fulfillment_status": "unfulfilled"
        "guest": "true"
        "editable": "true"
        "placeable": "false"
        "customer_email": "john@example.com"
        "language_code": "it"
        "currency_code": "EUR"
        "tax_included": "true"
        "tax_rate": "0.22"
        "freight_taxable": "true"
        "country_code": "IT"
        "shipping_country_code_lock": "IT"
        "coupon_code": "SUMMERDISCOUNT"
        "subtotal_amount_cents": "5000"
        "subtotal_amount_float": "50.0"
        "formatted_subtotal_amount": "€50,00"
        "shipping_amount_cents": "1200"
        "shipping_amount_float": "12.0"
        "formatted_shipping_amount": "€12,00"
        "payment_method_amount_cents": "0"
        "payment_method_amount_float": "0.0"
        "formatted_payment_method_amount": "€0,00"
        "discount_amount_cents": "-500"
        "discount_amount_float": "-5.0"
        "formatted_discount_amount": "-€5,00"
        "total_tax_amount_cents": "1028"
        "total_tax_amount_float": "10.28"
        "formatted_total_tax_amount": "€10,28"
        "subtotal_tax_amount_cents": "902"
        "subtotal_tax_amount_float": "9.02"
        "formatted_subtotal_tax_amount": "€9,02"
        "shipping_tax_amount_cents": "216"
        "shipping_tax_amount_float": "2.16"
        "formatted_shipping_tax_amount": "€2,16"
        "payment_method_tax_amount_cents": "0"
        "payment_method_tax_amount_float": "0.0"
        "formatted_payment_method_tax_amount": "€0,00"
        "discount_tax_amount_cents": "-90"
        "discount_tax_amount_float": "-0.9"
        "formatted_discount_tax_amount": "-€0,90"
        "total_amount_cents": "5700"
        "total_amount_float": "57.0"
        "formatted_total_amount": "€57,00"
        "total_taxable_amount_cents": "4672"
        "total_taxable_amount_float": "46.72"
        "formatted_total_taxable_amount": "€46,72"
        "subtotal_taxable_amount_cents": "4098"
        "subtotal_taxable_amount_float": "40.98"
        "formatted_subtotal_taxable_amount": "€40,98"
        "shipping_taxable_amount_cents": "984"
        "shipping_taxable_amount_float": "9.84"
        "formatted_shipping_taxable_amount": "€9,84"
        "payment_method_taxable_amount_cents": "0"
        "payment_method_taxable_amount_float": "0.0"
        "formatted_payment_method_taxable_amount": "€0,00"
        "discount_taxable_amount_cents": "-410"
        "discount_taxable_amount_float": "-4.10"
        "formatted_discount_taxable_amount": "-€4,10"
        "total_amount_with_taxes_cents": "5700"
        "total_amount_with_taxes_float": "57.00"
        "formatted_total_amount_with_taxes": "€57,00"
        "fees_amount_cents": "0"
        "fees_amount_float": "0.0"
        "formatted_fees_amount": "€0,00"
        "skus_count": "2"
        "line_item_options_count": "1"
        "shipments_count": "1"
        "payment_source_details": ""
        "token": "1c0994cc4e996e8c6ee56a2198f66f3c"
        "cart_url": "https://yourbrand.com/cart"
        "return_url": "https://yourbrand.com/"
        "terms_url": "https://yourbrand.com/terms"
        "privacy_url": "https://yourbrand.com/privacy"
        "checkout_url": "https://commerce.yourbrand.com/checkout/1c0994cc4e996e8c6ee56a2198f66f3c"
        "placed_at": "2018-01-01T12:00:00.000Z"
        "approved_at": "2018-01-01T12:00:00.000Z"
        "cancelled_at": "2018-01-01T12:00:00.000Z"
        "payment_updated_at": "2018-01-01T12:00:00.000Z"
        "fulfillment_updated_at": "2018-01-01T12:00:00.000Z"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
        "market": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/market",
              "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/market"
          }
        }
        "customer": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/customer",
              "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/customer"
          }
        }
        "shipping_address": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/shipping_address",
              "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/shipping_address"
          }
        }
        "billing_address": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/billing_address",
              "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/billing_address"
          }
        }
        "available_payment_methods": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/available_payment_methods",
              "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/available_payment_methods"
          }
        }
        "payment_method": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/payment_method",
              "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/payment_method"
          }
        }
        "payment_source": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/payment_source",
              "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/payment_source"
          }
        }
        "line_items": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/line_items",
              "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/line_items"
          }
        }
        "shipments": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/shipments",
              "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/shipments"
          }
        }
      },
      "meta": {
          "mode": "test"
      }
  }
}
```
{% endtab %}
{% endtabs %}
