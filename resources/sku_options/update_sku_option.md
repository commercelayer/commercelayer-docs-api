---
description: How to update an existing sku option via API
---

# Update a sku option

To update an existing sku option, send a `PATCH` request to the `/api/sku_options/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/sku_options/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**description** | `string` | Optional |
| attributes.**price_amount_cents** | `integer` | Optional, default is '0' |
| attributes.**delay_hours** | `integer` | Optional, default is '0' |
| attributes.**sku_code_regex** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**market** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the sku option identified by the ID "xYZkjABcde":

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
      "name": "Embossing"
    },
    "relationships": {
      "market": {
        "data": {
          "type": "markets",
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
    "type": "sku_options",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/sku_options/xYZkjABcde"
    },
    "attributes": {
      "name": "Embossing",
      "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
      "price_amount_cents": "1000",
      "price_amount_float": "10.00",
      "formatted_price_amount": "€10,00",
      "delay_hours": "48",
      "delay_days": "2",
      "sku_code_regex": "^(A|B).*$",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
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
