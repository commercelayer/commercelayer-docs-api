---
description: How to update an existing line item via API
---

# Update a line item

To update an existing line item, send a `PATCH` request to the `/api/line_items/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/line_items/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**sku_code** | `string` | Optional |
| attributes.**quantity** | `integer` | Required |
| attributes.**name** | `string` | Optional |
| attributes.**image_url** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the line item identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/line_items/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "line_items",
    "id": "xYZkjABcde",
    "attributes": {
      "sku_code": "TSHIRTMM000000FFFFFFXLXX"
      "quantity": "2"
      "name": "Black Men T-shirt with White Logo (XL)"
      "image_url": "https://img.yourdomain.com/skus/xYZkjABcde.png"
      "reference": "ANYREFEFERNCE"
      "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
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
    "type": "line_items",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/line_items/xYZkjABcde"
    },
    "attributes": {
      "sku_code": "TSHIRTMM000000FFFFFFXLXX",
      "quantity": "2",
      "currency_code": "EUR",
      "unit_amount_cents": "9900",
      "unit_amount_float": "99.0",
      "formatted_unit_amount": "€99,00",
      "options_amount_cents": "990",
      "options_amount_float": "9.9",
      "formatted_options_amount": "€9,90",
      "total_amount_cents": "18800",
      "total_amount_float": "188.0",
      "formatted_total_amount": "€188,00",
      "name": "Black Men T-shirt with White Logo (XL)",
      "image_url": "https://img.yourdomain.com/skus/xYZkjABcde.png",
      "tax_rate": "0.22",
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
      "reference": "ANYREFEFERNCE",
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
