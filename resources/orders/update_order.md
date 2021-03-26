---
description: How to update an existing order via API
---

# Update an order

To update an existing order, send a `PATCH` request to the `/api/orders/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://yourdomain.commercelayer.io**/api/orders/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**guest** | `boolean` | Optional |
| attributes.**customer\_email** | `string` | Optional |
| attributes.**customer\_password** | `string` | Optional |
| attributes.**language\_code** | `string` | Optional |
| attributes.**shipping\_country\_code\_lock** | `string` | Optional |
| attributes.**coupon\_code** | `string` | Optional |
| attributes.**gift\_card\_code** | `string` | Optional |
| attributes.**gift\_card\_or\_coupon\_code** | `string` | Optional |
| attributes.**cart\_url** | `string` | Optional |
| attributes.**return\_url** | `string` | Optional |
| attributes.**terms\_url** | `string` | Optional |
| attributes.**privacy\_url** | `string` | Optional |
| attributes.**\_archive** | `boolean, value is 'true'` | Optional |
| attributes.**\_unarchive** | `boolean, value is 'true'` | Optional |
| attributes.**\_place** | `boolean, value is 'true'` | Optional |
| attributes.**\_cancel** | `boolean, value is 'true'` | Optional |
| attributes.**\_approve** | `boolean, value is 'true'` | Optional |
| attributes.**\_approve\_and\_capture** | `boolean, value is 'true'` | Optional |
| attributes.**\_authorize** | `boolean, value is 'true'` | Optional |
| attributes.**\_authorization\_amount\_cents** | `integer` | Optional |
| attributes.**\_capture** | `boolean, value is 'true'` | Optional |
| attributes.**\_refund** | `boolean, value is 'true'` | Optional |
| attributes.**\_update\_taxes** | `boolean, value is 'true'` | Optional |
| attributes.**\_billing\_address\_clone\_id** | `string` | Optional |
| attributes.**\_shipping\_address\_clone\_id** | `string` | Optional |
| attributes.**\_customer\_payment\_source\_id** | `string` | Optional |
| attributes.**\_shipping\_address\_same\_as\_billing** | `boolean, value is 'true'` | Optional |
| attributes.**\_billing\_address\_same\_as\_shipping** | `boolean, value is 'true'` | Optional |
| attributes.**\_save\_payment\_source\_to\_customer\_wallet** | `boolean, value is 'true'` | Optional |
| attributes.**\_save\_shipping\_address\_to\_customer\_address\_book** | `boolean, value is 'true'` | Optional |
| attributes.**\_save\_billing\_address\_to\_customer\_address\_book** | `boolean, value is 'true'` | Optional |
| attributes.**\_refresh** | `boolean, value is 'true'` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**market** | `object` | Optional |
| relationships.**customer** | `object` | Optional |
| relationships.**shipping\_address** | `object` | Optional |
| relationships.**billing\_address** | `object` | Optional |
| relationships.**payment\_method** | `object` | Optional |
| relationships.**payment\_source** | `object` | Optional |

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
      "customer_email": "john@example.com"
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
    "id": "xYZkjABcde",
    "type": "orders",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde"
    },
    "attributes": {
      "number": 1234,
      "status": "draft",
      "payment_status": "unpaid",
      "fulfillment_status": "unfulfilled",
      "guest": true,
      "editable": true,
      "placeable": false,
      "customer_email": "john@example.com",
      "language_code": "it",
      "currency_code": "EUR",
      "tax_included": true,
      "tax_rate": 0.22,
      "freight_taxable": true,
      "requires_billing_info": false,
      "country_code": "IT",
      "shipping_country_code_lock": "IT",
      "coupon_code": "SUMMERDISCOUNT",
      "gift_card_code": "cc92c23e-967e-48b2-a323-59add603301f",
      "gift_card_or_coupon_code": "cc92c23e-967e-48b2-a323-59add603301f",
      "subtotal_amount_cents": 5000,
      "subtotal_amount_float": 50.0,
      "formatted_subtotal_amount": "€50,00",
      "shipping_amount_cents": 1200,
      "shipping_amount_float": 12.0,
      "formatted_shipping_amount": "€12,00",
      "payment_method_amount_cents": 0,
      "payment_method_amount_float": 0.0,
      "formatted_payment_method_amount": "€0,00",
      "discount_amount_cents": -500,
      "discount_amount_float": -5.0,
      "formatted_discount_amount": "-€5,00",
      "adjustment_amount_cents": 1500,
      "adjustment_amount_float": 15.0,
      "formatted_adjustment_amount": "€15,00",
      "gift_card_amount_cents": 1500,
      "gift_card_amount_float": 15.0,
      "formatted_gift_card_amount": "€15,00",
      "total_tax_amount_cents": 1028,
      "total_tax_amount_float": 10.28,
      "formatted_total_tax_amount": "€10,28",
      "subtotal_tax_amount_cents": 902,
      "subtotal_tax_amount_float": 9.02,
      "formatted_subtotal_tax_amount": "€9,02",
      "shipping_tax_amount_cents": 216,
      "shipping_tax_amount_float": 2.16,
      "formatted_shipping_tax_amount": "€2,16",
      "payment_method_tax_amount_cents": 0,
      "payment_method_tax_amount_float": 0.0,
      "formatted_payment_method_tax_amount": "€0,00",
      "adjustment_tax_amount_cents": 900,
      "adjustment_tax_amount_float": 9.0,
      "formatted_adjustment_tax_amount": "€9,00",
      "total_amount_cents": 5700,
      "total_amount_float": 57.0,
      "formatted_total_amount": "€57,00",
      "total_taxable_amount_cents": 4672,
      "total_taxable_amount_float": 46.72,
      "formatted_total_taxable_amount": "€46,72",
      "subtotal_taxable_amount_cents": 4098,
      "subtotal_taxable_amount_float": 40.98,
      "formatted_subtotal_taxable_amount": "€40,98",
      "shipping_taxable_amount_cents": 984,
      "shipping_taxable_amount_float": 9.84,
      "formatted_shipping_taxable_amount": "€9,84",
      "payment_method_taxable_amount_cents": 0,
      "payment_method_taxable_amount_float": 0.0,
      "formatted_payment_method_taxable_amount": "€0,00",
      "adjustment_taxable_amount_cents": 120,
      "adjustment_taxable_amount_float": 1.2,
      "formatted_adjustment_taxable_amount": "€1,20",
      "total_amount_with_taxes_cents": 5700,
      "total_amount_with_taxes_float": 57.0,
      "formatted_total_amount_with_taxes": "€57,00",
      "fees_amount_cents": 0,
      "fees_amount_float": 0.0,
      "formatted_fees_amount": "€0,00",
      "duty_amount_cents": 0,
      "duty_amount_float": 0.0,
      "formatted_duty_amount": "€0,00",
      "skus_count": 2,
      "line_item_options_count": 1,
      "shipments_count": 1,
      "payment_source_details": null,
      "token": "1c0994cc4e996e8c6ee56a2198f66f3c",
      "cart_url": "https://yourdomain.com/cart",
      "return_url": "https://yourdomain.com/",
      "terms_url": "https://yourdomain.com/terms",
      "privacy_url": "https://yourdomain.com/privacy",
      "checkout_url": "https://yourdomain.commercelayer.io/checkout/1c0994cc4e996e8c6ee56a2198f66f3c",
      "placed_at": "2018-01-01T12:00:00.000Z",
      "approved_at": "2018-01-01T12:00:00.000Z",
      "cancelled_at": "2018-01-01T12:00:00.000Z",
      "payment_updated_at": "2018-01-01T12:00:00.000Z",
      "fulfillment_updated_at": "2018-01-01T12:00:00.000Z",
      "archived_at": "2018-01-01T12:00:00.000Z",
      "expires_at": "2018-01-01T12:00:00.000Z",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "market": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/market",
          "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/market"
        }
      },
      "customer": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/customer",
          "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/customer"
        }
      },
      "shipping_address": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/shipping_address",
          "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/shipping_address"
        }
      },
      "billing_address": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/billing_address",
          "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/billing_address"
        }
      },
      "available_payment_methods": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/available_payment_methods",
          "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/available_payment_methods"
        }
      },
      "available_customer_payment_sources": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/available_customer_payment_sources",
          "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/available_customer_payment_sources"
        }
      },
      "payment_method": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/payment_method",
          "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/payment_method"
        }
      },
      "payment_source": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/payment_source",
          "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/payment_source"
        }
      },
      "line_items": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/line_items",
          "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/line_items"
        }
      },
      "shipments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/shipments",
          "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/shipments"
        }
      },
      "transactions": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/transactions",
          "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/transactions"
        }
      },
      "authorizations": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/authorizations",
          "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/authorizations"
        }
      },
      "captures": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/captures",
          "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/captures"
        }
      },
      "voids": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/voids",
          "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/voids"
        }
      },
      "refunds": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/refunds",
          "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/refunds"
        }
      },
      "attachments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/relationships/attachments",
          "related": "https://yourdomain.commercelayer.io/api/orders/xYZkjABcde/attachments"
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

