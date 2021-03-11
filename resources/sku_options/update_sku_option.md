---
description: How to update an existing SKU option via API
---

# Update a SKU option

To update an existing SKU option, send a `PATCH` request to the `/api/sku_options/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/sku_options/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**name** | `string` | Optional |
| attributes.**description** | `string` | Optional |
| attributes.**price_amount_cents** | `integer` | Optional |
| attributes.**delay_hours** | `integer` | Optional |
| attributes.**sku_code_regex** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**market** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the SKU option identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/sku_options/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "sku_options",
    "id": "xYZkjABcde",
    "attributes": {
      "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
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
    "type": "sku_options",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/sku_options/xYZkjABcde"
    },
    "attributes": {
      "name": "Embossing",
      "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
      "price_amount_cents": 1000,
      "price_amount_float": 10.0,
      "formatted_price_amount": "€10,00",
      "delay_hours": 48,
      "delay_days": 2,
      "sku_code_regex": "^(A|B).*$",
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
          "self": "https://yourdomain.commercelayer.io/api/sku_options/xYZkjABcde/relationships/market",
          "related": "https://yourdomain.commercelayer.io/api/sku_options/xYZkjABcde/market"
        }
      },
      "attachments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/sku_options/xYZkjABcde/relationships/attachments",
          "related": "https://yourdomain.commercelayer.io/api/sku_options/xYZkjABcde/attachments"
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

