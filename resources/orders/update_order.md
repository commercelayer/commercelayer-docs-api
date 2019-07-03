---
description: How to update an existing order via API
---

# Update an order

To update an existing order, send a `PATCH` request to the `/api/orders/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/orders/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**guest** | `boolean` | Optional |
| attributes.**customer_email** | `string` | Optional |
| attributes.**customer_password** | `string` | Optional |
| attributes.**language_code** | `string` | Optional, default is 'en' |
| attributes.**shipping_country_code_lock** | `string` | Optional |
| attributes.**coupon_code** | `string` | Optional |
| attributes.**cart_url** | `string` | Optional |
| attributes.**return_url** | `string` | Optional |
| attributes.**terms_url** | `string` | Optional |
| attributes.**privacy_url** | `string` | Optional |
| attributes.**_place** | `integer, value is '1'` |  |
| attributes.**_cancel** | `integer, value is '1'` |  |
| attributes.**_approve** | `integer, value is '1'` |  |
| attributes.**_capture** | `integer, value is '1'` |  |
| attributes.**_refund** | `integer, value is '1'` |  |
| attributes.**_update_taxes** | `integer, value is '1'` |  |
| attributes.**_billing_address_clone_id** | `integer` |  |
| attributes.**_shipping_address_clone_id** | `integer` |  |
| attributes.**_customer_payment_source_id** | `integer` | Optional |
| attributes.**_shipping_address_same_as_billing** | `integer, value is '1'` | Optional |
| attributes.**_billing_address_same_as_shipping** | `integer, value is '1'` | Optional |
| attributes.**_save_payment_source_to_customer_wallet** | `integer, value is '1'` | Optional |
| attributes.**_save_shipping_address_to_customer_address_book** | `integer, value is '1'` | Optional |
| attributes.**_save_billing_address_to_customer_address_book** | `integer, value is '1'` | Optional |
| attributes.**_refresh** | `integer, value is '1'` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**market** | `object` | Required |
| relationships.**customer** | `object` | Optional |
| relationships.**shipping_address** | `object` | Optional |
| relationships.**billing_address** | `object` | Optional |
| relationships.**payment_method** | `object` | Optional |
| relationships.**payment_source** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the order identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/orders/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "orders",
    "id": "xYZkjABcde",
    "attributes": {
      "guest": "true"
      "customer_email": "john@example.com"
      "customer_password": "secret"
      "language_code": "it"
      "shipping_country_code_lock": "IT"
      "coupon_code": "SUMMERDISCOUNT"
      "cart_url": "https://yourbrand.com/cart"
      "return_url": "https://yourbrand.com/"
      "terms_url": "https://yourbrand.com/terms"
      "privacy_url": "https://yourbrand.com/privacy"
      "_place": "1"
      "_cancel": "1"
      "_approve": "1"
      "_capture": "1"
      "_refund": "1"
      "_update_taxes": "1"
      "_billing_address_clone_id": "1234"
      "_shipping_address_clone_id": "1234"
      "_customer_payment_source_id": "1234"
      "_shipping_address_same_as_billing": "1"
      "_billing_address_same_as_shipping": "1"
      "_save_payment_source_to_customer_wallet": "1"
      "_save_shipping_address_to_customer_address_book": "1"
      "_save_billing_address_to_customer_address_book": "1"
      "_refresh": "1"
      "reference": "ANYREFEFERNCE"
      "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
      "market": {
        "data": {
          "type": "markets",
          "id": "QWERtyUpBa"
        }
      }
      "customer": {
        "data": {
          "type": "customers",
          "id": "QWERtyUpBa"
        }
      }
      "shipping_address": {
        "data": {
          "type": "addresses",
          "id": "QWERtyUpBa"
        }
      }
      "billing_address": {
        "data": {
          "type": "addresses",
          "id": "QWERtyUpBa"
        }
      }
      "payment_method": {
        "data": {
          "type": "payment_methods",
          "id": "QWERtyUpBa"
        }
      }
      "payment_source": {
        "data": {
          "type": "payment_sources",
          "id": "QWERtyUpBa"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning the updated resource object:

```javascript
{
  "data": {
    "id": "{{order_id}}",
    "type": "orders",
    "links": {
      "self": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}"
    },
    "attributes": {
      "number": 1234,
      "status": "draft",
      "payment_status": "unpaid",
      "fulfillment_status": "unfulfilled",
      "guest": "true",
      "editable": "true",
      "placeable": "false",
      "customer_email": "john@example.com",
      "language_code": "it",
      "currency_code": "EUR",
      "tax_included": "true",
      "tax_rate": "0.22",
      "freight_taxable": "true",
      "country_code": "IT",
      "shipping_country_code_lock": "IT",
      "coupon_code": "SUMMERDISCOUNT",
      "subtotal_amount_cents": "5000",
      "subtotal_amount_float": "50.0",
      "formatted_subtotal_amount": "€50,00",
      "shipping_amount_cents": "1200",
      "shipping_amount_float": "12.0",
      "formatted_shipping_amount": "€12,00",
      "payment_method_amount_cents": "0",
      "payment_method_amount_float": "0.0",
      "formatted_payment_method_amount": "€0,00",
      "discount_amount_cents": "-500",
      "discount_amount_float": "-5.0",
      "formatted_discount_amount": "-€5,00",
      "total_tax_amount_cents": "1028",
      "total_tax_amount_float": "10.28",
      "formatted_total_tax_amount": "€10,28",
      "subtotal_tax_amount_cents": "902",
      "subtotal_tax_amount_float": "9.02",
      "formatted_subtotal_tax_amount": "€9,02",
      "shipping_tax_amount_cents": "216",
      "shipping_tax_amount_float": "2.16",
      "formatted_shipping_tax_amount": "€2,16",
      "payment_method_tax_amount_cents": "0",
      "payment_method_tax_amount_float": "0.0",
      "formatted_payment_method_tax_amount": "€0,00",
      "discount_tax_amount_cents": "-90",
      "discount_tax_amount_float": "-0.9",
      "formatted_discount_tax_amount": "-€0,90",
      "total_amount_cents": "5700",
      "total_amount_float": "57.0",
      "formatted_total_amount": "€57,00",
      "total_taxable_amount_cents": "4672",
      "total_taxable_amount_float": "46.72",
      "formatted_total_taxable_amount": "€46,72",
      "subtotal_taxable_amount_cents": "4098",
      "subtotal_taxable_amount_float": "40.98",
      "formatted_subtotal_taxable_amount": "€40,98",
      "shipping_taxable_amount_cents": "984",
      "shipping_taxable_amount_float": "9.84",
      "formatted_shipping_taxable_amount": "€9,84",
      "payment_method_taxable_amount_cents": "0",
      "payment_method_taxable_amount_float": "0.0",
      "formatted_payment_method_taxable_amount": "€0,00",
      "discount_taxable_amount_cents": "-410",
      "discount_taxable_amount_float": "-4.10",
      "formatted_discount_taxable_amount": "-€4,10",
      "total_amount_with_taxes_cents": "5700",
      "total_amount_with_taxes_float": "57.00",
      "formatted_total_amount_with_taxes": "€57,00",
      "fees_amount_cents": "0",
      "fees_amount_float": "0.0",
      "formatted_fees_amount": "€0,00",
      "skus_count": "2",
      "line_item_options_count": "1",
      "shipments_count": "1",
      "payment_source_details": null,
      "token": "1c0994cc4e996e8c6ee56a2198f66f3c",
      "cart_url": "https://yourbrand.com/cart",
      "return_url": "https://yourbrand.com/",
      "terms_url": "https://yourbrand.com/terms",
      "privacy_url": "https://yourbrand.com/privacy",
      "checkout_url": "https://commerce.yourbrand.com/checkout/1c0994cc4e996e8c6ee56a2198f66f3c",
      "placed_at": "2018-01-01T12:00:00.000Z",
      "approved_at": "2018-01-01T12:00:00.000Z",
      "cancelled_at": "2018-01-01T12:00:00.000Z",
      "payment_updated_at": "2018-01-01T12:00:00.000Z",
      "fulfillment_updated_at": "2018-01-01T12:00:00.000Z",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "market": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}/relationships/market",
          "related": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}/market"
        }
      },
      "customer": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}/relationships/customer",
          "related": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}/customer"
        }
      },
      "shipping_address": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}/relationships/shipping_address",
          "related": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}/shipping_address"
        }
      },
      "billing_address": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}/relationships/billing_address",
          "related": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}/billing_address"
        }
      },
      "available_payment_methods": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}/relationships/available_payment_methods",
          "related": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}/available_payment_methods"
        }
      },
      "payment_method": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}/relationships/payment_method",
          "related": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}/payment_method"
        }
      },
      "payment_source": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}/relationships/payment_source",
          "related": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}/payment_source"
        }
      },
      "line_items": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}/relationships/line_items",
          "related": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}/line_items"
        }
      },
      "shipments": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}/relationships/shipments",
          "related": "https://{{subdomain}}.commercelayer.io/api/orders/{{order_id}}/shipments"
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
