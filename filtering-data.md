---
description: How to add filters to your requests
---

# Filtering data

When you fetch a collection of resources, you can add filters to further refine the results, using the `filter[q]` query parameter. 

{% hint style="info" %}
Filters can be combined according to an "AND" logic to send requests that fetch collections of resources meeting all the criteria within a set of multiple filters \([see example](filtering-data.md#combining-filters)\).
{% endhint %}

Each single filter query is built like this:

```http
filter[q][{{predicate}}]={{value}}
```

Here, `value` stands for the value that the fetched resources have to match, while the `predicate`parameter has this format:

```text
{{attributes}}_{{matcher}}
```

Where `attributes` is a set of one or more attributes and `matcher` represents the condition to be met by the query.

{% hint style="info" %}
Attributes can be combined according to an "OR" logic and can belong to either the fetched resource or to one of its relationships \([see example](filtering-data.md#using-filters-that-belong-to-a-resource-relationship)\). 
{% endhint %}

### List of Predicates

You can find here below the complete list of all possible predicates:

| Predicate | Description | Example |
| :--- | :--- | :--- |
| `*_eq` | The attribute is equal to the filter value | `filter[q][name_eq]=red+handbag` |
| `*_not_eq` | The attribute is not equal to the filter value | `filter[q][status_not_eq]=prospect` |
| `*_matches` | The attribute matches the filter value with "LIKE" operator | `filter[q][email_matches]=%@gmail.com` |
| `*_does_not_match` | The attribute does not match the filter value with "LIKE" operator | `filter[q][email_does_not_match]=%@hotmail.com` |
| `*_matches_any` | The attribute matches all of the filter values \(comma-separated\) with "LIKE" operator | `filter[q][email_matches_any]=%@gmail.com,%@hotmail.com` |
| `*_matches_all` | The attribute matches all of the filter values \(comma-separated\) with "LIKE" operator | `filter[q][name_matches_all]=%Pink%,%Logo%` |
| `*_does_not_match_any` | The attribute does not match any of the filter values \(comma-separated\) with "LIKE" operator | `filter[q][email_does_not_match_any]=%Pink%,%Logo%` |
| `*_does_not_match_all` | The attribute matches none of the filter values \(comma-separated\) with "LIKE" operator | `filter[q][email_does_not_match_all]=%@gmail.com,%@hotmail.com` |
| `*_lt` | The attribute is less than the filter value | `filter[q][amount_cents_lt]=2000` |
| `*_lteq` | The attribute is less than or equal to the filter value | `filter[q][amount_cents_lteq]=2000` |
| `*_gt` | The attribute is greater than the filter value | `filter[q][created_at_gt]=2019-01-01T01:00:00.000Z` |
| `*_gteq` | The attribute is greater than or equal to the filter value | `filter[q][updated_at_gteq]=2019-01-02T10:30:00.000Z` |
| `*_present` | The attribute is not null and not empty | `filter[q][description_present]=false` |
| `*_blank` | The attribute is null or empty | `filter[q][description_blank]=true` |
| `*_null` | The attribute is null | `filter[q][reference_null]=true` |
| `*_not_null` | The attribute is not null | `filter[q][reference_not_null]=false` |
| `*_in` | The attribute matches none of the filter values \(comma-separated\) | `filter[q][status_in]=placed,pending` |
| `*_not_in` | The attribute matches none of the filter values \(comma-separated\) | `filter[q][status_not_in]=approved,cancelled` |
| `*_lt_any` | The attribute is less than any of the filter values \(comma-separated\) | `filter[q][amount_cents_lt_any]=1500,700,3400` |
| `*_lteq_any` | The attribute is less than or equal to any of the filter values \(comma-separated\) | `filter[q][amount_cents_lteq_any]=1500,700,3400` |
| `*_gt_any` | The attribute is greater than any of the filter values \(comma-separated\) | `filter[q][amount_cents_gt_any]=1500,700,3400` |
| `*_gteq_any` | The attribute is greater than or qual to any of the filter values \(comma-separated\) | `filter[q][amount_cents_gteq_any]=1500,700,3400` |
| `*_lt_all` | The attribute is less than all of the filter values \(comma-separated\) | `filter[q][amount_cents_lt_all]=1500,700,3400` |
| `*_lteq_all` | The attribute is less than or equal to all of the filter values \(comma-separated\) | `filter[q][amount_cents_lteq_all]=1500,700,3400` |
| `*_gt_all` | The attribute is greater than all of the filter values \(comma-separated\) | `filter[q][amount_cents_gt_all]=1500,700,3400` |
| `*_gteq_all` | The attribute is greater or equal to all of the filter values \(comma-separated\) | `filter[q][amount_cents_gteq_all]=1500,700,3400` |
| `*_not_eq_all` | The attribute is equal to none of the filter values \(comma-separated\) | `filter[q][amount_cents_not_eq_all]=1000,2000,3000` |
| `*_start` | The attribute starts with the filter value \(comma-separated\) | `filter[q][email_start]=patrick` |
| `*_not_start` | The attribute does not start with the filter value \(comma-separated\) | `filter[q][email_not_start]=mary` |
| `*_start_any` | The attribute starts with any of the filter values \(comma-separated\) | `filter[q][email_start_any]=patrick,mary` |
| `*_start_all` | The attribute starts with all of the filter values \(comma-separated\) | `filter[q][email_start_all]=patrick,pat` |
| `*_not_start_any` | The attribute does not start with any of the filter values \(comma-separated\) | `filter[q][email_not_start_any]=patrick,pat` |
| `*_not_start_all` | The attribute starts with none of the filter values \(comma-separated\) | `filter[q][email_not_start_all]=patrick,mary` |
| `*_end` | The attribute ends with the filter value | `filter[q][email_end]=.com` |
| `*_not_end` | The attribute does not end with the filter value | `filter[q][email_not_end]=.it` |
| `*_end_any` | The attribute ends with any of the filter values \(comma-separated\) | `filter[q][email_end_any]=.com,.it` |
| `*_end_all` | The attribute ends with all of the filter values \(comma-separated\) | `filter[q][email_end_all]=.com,gmail.com` |
| `*_not_end_any` | The attribute does not end with any of the filter values \(comma-separated\) | `filter[q][email_not_end_any]=.com,gmail.com` |
| `*_not_end_all` | The attribute ends with none of the filter values \(comma-separated\) | `filter[q][email_not_end_all]=.com,.it` |
| `*_cont` | The attribute contains the filter value | `filter[q][name_cont]=unisex` |
| `*_not_cont` | The attribute does not contains the filter value | `filter[q][name_not_cont]=black` |
| `*_cont_any` | The attribute contains any of the filter values \(comma-separated\) | `filter[q][name_cont_any]=black,white` |
| `*_cont_all` | The attribute contains all of the filter values \(comma-separated\) | `filter[q][name_cont_all]=black,sleeve` |
| `*_not_cont_all` | The attribute contains none of the filter values \(comma-separated\) | `filter[q][sku_code_not_cont_all]=TSHIRT,SXXX` |
| `*_true` | The attribute is true | `filter[q][tax_included_true]=true` |
| `*_false` | The attribute is false | `filter[q][tax_included_false]=true` |

{% hint style="warning" %}
In case of comma-separated sets of values \(e.g. `*_in`, `*_matches_all`, `*_start_any` etc.\), pay attention to avoid whitespaces before or after each comma.
{% endhint %}

### Examples

#### Combining filters

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of SKUs that have been created within a specific time range:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/skus?filter[q][created_at_gt]=2018-01-01&filter[q][created_at_lt]=2018-01-31 \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a paginated collection ****of the resource objects that match the filter query:

```javascript
{
  "data": [
    {
      "id": "xYZkjABcde",
      "type": "skus",
      "links": {...},
      "attributes": {
        "code": "TSHIRTMM000000FFFFFFXLXX",
        "name": "Black Men T-shirt with White Logo (XL)",
        "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        "image_url": "https://img.yourdomain.com/skus/xYZkjABcde.png",
        "tag_names": "Men, Black, XL",
        "pieces_per_pack": "6",
        "weight": "300",
        "unit_of_weight": "gr",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANYREFEFERNCE",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "shipping_category": {
          "links": {...}
        },
        "prices": {
          "links": {...}
        },
        "stock_items": {
          "links": {...}
        },
        "delivery_lead_times": {
          "links": {...}
        },
        "sku_options": {
          "links": {...}
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 skus (first page)"
    }
  ],
  "meta": {
    "record_count": 50,
    "page_count": 5
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/skus?filter[q][created_at_gt]=2018-01-01&filter[q][created_at_lt]=2018-01-31&page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/skus?filter[q][created_at_gt]=2018-01-01&filter[q][created_at_lt]=2018-01-31&page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/skus?filter[q][created_at_gt]=2018-01-01&filter[q][created_at_lt]=2018-01-31&page[number]=5&page[size]=10"
  }
}
```

{% page-ref page="pagination.md" %}
{% endtab %}
{% endtabs %}

#### Combining filters and attributes

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of orders that have been created or updated after a specific date and that haven't been paid yet:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/orders?filter[q][created_at_or_updated_at_gt]=2018-01-01&filter[q][payment_status_eq]=unpaid \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a paginated collection ****of the resource objects that match the filter query:

```javascript
{
  "data": [
    {
      "id": "xYZkjABcde",
      "type": "orders",
      "links": {...},
      "attributes": {
        "status": "pending",
        "payment_status": "unpaid",
        "fulfillment_status": "unfulfilled",
        "guest": true,
        "editable": true,
        "placeable": false,
        "customer_email": "john@example.com",
        "language_code": "en",
        "currency_code": "EUR",
        "tax_included": true,
        "tax_rate": null,
        "freight_taxable": null,
        "country_code": null,
        "shipping_country_code_lock": null,
        "coupon_code": null,
        "subtotal_amount_cents": 4400,
        "subtotal_amount_float": 44,
        "formatted_subtotal_amount": "€44,00",
        "shipping_amount_cents": 0,
        "shipping_amount_float": 0,
        "formatted_shipping_amount": "€0,00",
        "payment_method_amount_cents": 0,
        "payment_method_amount_float": 0,
        "formatted_payment_method_amount": "€0,00",
        "discount_amount_cents": 0,
        "discount_amount_float": 0,
        "formatted_discount_amount": "€0,00",
        "total_tax_amount_cents": 0,
        "total_tax_amount_float": 0,
        "formatted_total_tax_amount": "€0,00",
        "subtotal_tax_amount_cents": 0,
        "subtotal_tax_amount_float": 0,
        "formatted_subtotal_tax_amount": "€0,00",
        "shipping_tax_amount_cents": 0,
        "shipping_tax_amount_float": 0,
        "formatted_shipping_tax_amount": "€0,00",
        "payment_method_tax_amount_cents": 0,
        "payment_method_tax_amount_float": 0,
        "formatted_payment_method_tax_amount": "€0,00",
        "discount_tax_amount_cents": 0,
        "discount_tax_amount_float": 0,
        "formatted_discount_tax_amount": "€0,00",
        "total_amount_cents": 4400,
        "total_amount_float": 44,
        "formatted_total_amount": "€44,00",
        "total_taxable_amount_cents": 4400,
        "total_taxable_amount_float": 44,
        "formatted_total_taxable_amount": "€44,00",
        "subtotal_taxable_amount_cents": 4400,
        "subtotal_taxable_amount_float": 44,
        "formatted_subtotal_taxable_amount": "€44,00",
        "shipping_taxable_amount_cents": 0,
        "shipping_taxable_amount_float": 0,
        "formatted_shipping_taxable_amount": "€0,00",
        "payment_method_taxable_amount_cents": 0,
        "payment_method_taxable_amount_float": 0,
        "formatted_payment_method_taxable_amount": "€0,00",
        "discount_taxable_amount_cents": 0,
        "discount_taxable_amount_float": 0,
        "formatted_discount_taxable_amount": "€0,00",
        "total_amount_with_taxes_cents": 4400,
        "total_amount_with_taxes_float": 44,
        "formatted_total_amount_with_taxes": "€44,00",
        "fees_amount_cents": 0,
        "fees_amount_float": 0,
        "formatted_fees_amount": "€0,00",
        "skus_count": 2,
        "line_item_options_count": 0,
        "shipments_count": 0,
        "payment_source_details": null,
        "token": "order-token",
        "cart_url": null,
        "return_url": null,
        "terms_url": null,
        "privacy_url": null,
        "checkout_url": "https://yourdomain.commercelayer.io/checkout/order-token",
        "placed_at": null,
        "approved_at": null,
        "cancelled_at": null,
        "payment_updated_at": null,
        "fulfillment_updated_at": null,
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": null,
        "metadata": {}
      },
      "relationships": {
        "market": {
          "links": {...}
        },
        "customer": {
          "links": {...}
        },
        "shipping_address": {
          "links": {...}
        },
        "billing_address": {
          "links": {...}
        },
        "available_payment_methods": {
          "links": {...}
        },
        "payment_method": {
          "links": {...}
        },
        "payment_source": {
          "links": {...}
        },
        "line_items": {
          "links": {...}
        },
        "shipments": {
          "links": {...}
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 orders (first page)"
    }
  ],
  "meta": {
      "record_count": 10,
      "page_count": 1
  },
  "links": {
      "first": "https://yourdomain.commercelayer.io/api/orders?filter[q][created_at_or_updated_at_gt]=2018-01-01&filter[q][payment_status_eq]=unpaid&page[number]=1&page[size]=10",
      "last": "https://yourdomain.commercelayer.io/api/orders?filter[q][created_at_or_updated_at_gt]=2018-01-01&filter[q][payment_status_eq]=unpaid&page[number]=1&page[size]=10"
  }
}
```

{% page-ref page="pagination.md" %}
{% endtab %}
{% endtabs %}

#### Using filters that belong to a resource relationship

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of SKUs whose name, code or shipping category name starts with the string "TSHIRT" \(as mentioned above, the attribute`shipping_category_name` here belongs to a relationship and filters the list of SKUs by the name of the associated shipping category\):

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/skus?filter[q][name_or_code_or_shipping_category_name_start]=TSHIRT \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a paginated collection ****of the resource objects that match the filter query:

```javascript
{
  "data": [
    {
      "id": "xYZkjABcde",
      "type": "skus",
      "links": {...},
      "attributes": {
        "code": "TSHIRTMM000000FFFFFFXLXX",
        "name": "Black Men T-shirt with White Logo (XL)",
        "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        "image_url": "https://img.yourdomain.com/skus/xYZkjABcde.png",
        "tag_names": "Men, Black, XL",
        "pieces_per_pack": "6",
        "weight": "300",
        "unit_of_weight": "gr",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANYREFEFERNCE",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "shipping_category": {
          "links": {...}
        },
        "prices": {
          "links": {...}
        },
        "stock_items": {
          "links": {...}
        },
        "delivery_lead_times": {
          "links": {...}
        },
        "sku_options": {
          "links": {...}
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 skus (first page)"
    }
  ],
  "meta": {
    "record_count": 20,
    "page_count": 2
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/skus?filter[q][name_or_code_or_shipping_category_name_start]=TSHIRT&page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/skus?filter[q][name_or_code_or_shipping_category_name_start]=TSHIRT&page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/skus?filter[q][name_or_code_or_shipping_category_name_start]=TSHIRT&page[number]=2&page[size]=10"
  }
}
```

{% page-ref page="pagination.md" %}
{% endtab %}
{% endtabs %}

