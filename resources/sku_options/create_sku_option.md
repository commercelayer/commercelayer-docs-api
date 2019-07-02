---
description: How to create A sku option via API
---

# Create A sku option

To create a new sku option, send a `POST` request to the `/api/sku_options` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

```text
**POST** https://yourdomain.commercelayer.io**/api/sku_options**
```

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | required |
| attributes.**description** | `string` | optional |
| attributes.**price_amount_cents** | `integer` | optional, default is '0' |
| attributes.**price_amount_float** | `float` |  |
| attributes.**formatted_price_amount** | `string` |  |
| attributes.**delay_hours** | `integer` | optional, default is '0' |
| attributes.**delay_days** | `integer` |  |
| attributes.**sku_code_regex** | `string` | optional |
| attributes.**id** | `string` | required |
| attributes.**created_at** | `datetime` | required |
| attributes.**updated_at** | `datetime` | required |
| attributes.**reference** | `string` | optional |
| attributes.**metadata** | `object` | optional |
| relationships.**market** | `has_one` | required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new sku option:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/sku_options \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "sku_options",
    "attributes": {
      "name": "Embossing"
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
On success, the API responds with a `201 Created` status code, returning the created `sku option` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "sku_options",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/sku_options/xYZkjABcde"
    },
    "attributes": {
        "name": "Embossing"
        "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
        "price_amount_cents": "1000"
        "price_amount_float": "10.00"
        "formatted_price_amount": "€10,00"
        "delay_hours": "48"
        "delay_days": "2"
        "sku_code_regex": "^(A|B).*$"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
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
