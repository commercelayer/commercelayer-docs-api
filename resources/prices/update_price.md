---
description: How to update an existing price via API
---

# Update a price

To update an existing price, send a `PATCH` request to the `/api/prices/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://yourdomain.commercelayer.io**/api/prices/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**sku\_code** | `string` | Optional |
| attributes.**amount\_cents** | `integer` | Optional |
| attributes.**compare\_at\_amount\_cents** | `integer` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**price\_list** | `object` | Optional |
| relationships.**sku** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the price identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/prices/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "prices",
    "id": "xYZkjABcde",
    "attributes": {
      "amount_cents": "10000",
      "compare_at_amount_cents": "13000"
    },
    "relationships": {
      "price_list": {
        "data": {
          "type": "price_lists",
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
    "id": "xYZkjABcde",
    "type": "prices",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde"
    },
    "attributes": {
      "currency_code": "EUR",
      "sku_code": "TSHIRTMM000000FFFFFFXLXX",
      "amount_cents": "10000",
      "amount_float": "100.0",
      "formatted_amount": "€100,00",
      "compare_at_amount_cents": "13000",
      "compare_at_amount_float": "130.00",
      "formatted_compare_at_amount": "€130,00",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "price_list": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde/relationships/price_list",
          "related": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde/price_list"
        }
      },
      "sku": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde/relationships/sku",
          "related": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde/sku"
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

