---
description: How to fetch a collection of line items via API
---

# List all line items

To fetch a collection of line items, send a `GET` request to the `/api/line_items` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/line_items**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of line items:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/line_items/ \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a paginated collection of resource objects:

```javascript
{
  "data": [
    {
      "id": "xYZkjABcde",
      "type": "line_items",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/line_items/xYZkjABcde"
      },
      "attributes": {
        "sku_code": "TSHIRTMM000000FFFFFFXLXX",
        "bundle_code": "BUNDLEMM000000FFFFFFXLXX",
        "quantity": 4,
        "currency_code": "EUR",
        "unit_amount_cents": 9900,
        "unit_amount_float": 99.0,
        "formatted_unit_amount": "€99,00",
        "options_amount_cents": 990,
        "options_amount_float": 9.9,
        "formatted_options_amount": "€9,90",
        "discount_cents": -900,
        "discount_float": 9.0,
        "formatted_discount": "€9,00",
        "total_amount_cents": 18800,
        "total_amount_float": 188.0,
        "formatted_total_amount": "€188,00",
        "tax_amount_cents": 1880,
        "tax_amount_float": 18.8,
        "formatted_tax_amount": "€18,80",
        "name": "Black Men T-shirt with White Logo (XL)",
        "image_url": "https://img.yourdomain.com/skus/xYZkjABcde.png",
        "discount_breakdown": {
          "41": {
            "cents": -900,
            "weight": 0.416
          }
        },
        "tax_rate": 0.22,
        "tax_breakdown": {
          "id": "1234",
          "city_amount": "0.0",
          "state_amount": 6.6,
          "city_tax_rate": 0.0,
          "county_amount": 2.78,
          "taxable_amount": 139.0,
          "county_tax_rate": 0.02,
          "tax_collectable": 10.08,
          "special_tax_rate": 0.005,
          "combined_tax_rate": 0.0725,
          "city_taxable_amount": 0.0,
          "state_sales_tax_rate": 0.0475,
          "state_taxable_amount": 139.0,
          "county_taxable_amount": 139.0,
          "special_district_amount": 0.7,
          "special_district_taxable_amount": 139.0
        },
        "item_type": "sku",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "order": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/line_items/xYZkjABcde/relationships/order",
            "related": "https://yourdomain.commercelayer.io/api/line_items/xYZkjABcde/order"
          }
        },
        "item": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/line_items/xYZkjABcde/relationships/item",
            "related": "https://yourdomain.commercelayer.io/api/line_items/xYZkjABcde/item"
          }
        },
        "line_item_options": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/line_items/xYZkjABcde/relationships/line_item_options",
            "related": "https://yourdomain.commercelayer.io/api/line_items/xYZkjABcde/line_item_options"
          }
        },
        "shipment_line_items": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/line_items/xYZkjABcde/relationships/shipment_line_items",
            "related": "https://yourdomain.commercelayer.io/api/line_items/xYZkjABcde/shipment_line_items"
          }
        },
        "stock_line_items": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/line_items/xYZkjABcde/relationships/stock_line_items",
            "related": "https://yourdomain.commercelayer.io/api/line_items/xYZkjABcde/stock_line_items"
          }
        },
        "stock_transfers": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/line_items/xYZkjABcde/relationships/stock_transfers",
            "related": "https://yourdomain.commercelayer.io/api/line_items/xYZkjABcde/stock_transfers"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 line_items (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/line_items?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/line_items?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/line_items?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of line items can be sorted by the following attributes:

* `total_amount_cents`
* `tax_amount_cents`
* `item_type`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

