---
description: How to create A price list via API
---

# Create A price list

To create a new price list, send a `POST` request to the `/api/price_lists` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https\://yourdomain.commercelayer.io**/api/price_lists**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | required |
| attributes.**currency_code** | `string` | required |
| attributes.**tax_included** | `boolean` | optional, default is 'true' |
| attributes.**id** | `string` | required |
| attributes.**created_at** | `datetime` | required |
| attributes.**updated_at** | `datetime` | required |
| attributes.**reference** | `string` | optional |
| attributes.**metadata** | `object` | optional |
| relationships.**prices** | `has_many` |  |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new price list:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/price_lists \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "price_lists",
    "attributes": {
      "name": "EU Price list"
      "currency_code": "EUR"
    },
    "relationships": {
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `price list` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "price_lists",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/price_lists/xYZkjABcde"
    },
    "attributes": {
        "name": "EU Price list"
        "currency_code": "EUR"
        "tax_included": "true"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
        "prices": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/price_lists/xYZkjABcde/relationships/prices",
              "related": "https://yourdomain.commercelayer.io/api/price_lists/xYZkjABcde/prices"
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
