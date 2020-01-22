---
description: How to create a gift card via API
---

# Create a gift card

To create a new gift card, send a `POST` request to the `/api/gift_cards` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/gift_cards**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**code** | `string` |  |
| attributes.**currency_code** | `string` | Required |
| attributes.**balance_cents** | `integer` | Required |
| attributes.**balance_max_cents** | `string` | Optional |
| attributes.**single_use** | `boolean` | Optional, default is 'false' |
| attributes.**rechargeable** | `boolean` | Optional, default is 'true' |
| attributes.**image_url** | `string` | Optional |
| attributes.**expires_at** | `datetime` | Optional, default is 'null' |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**recipient_email** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**market** | `object` | Optional |
| relationships.**gift_card_recipient** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new gift card:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/gift_cards \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "gift_cards",
    "attributes": {
      "currency_code": "EUR",
      "balance_cents": "15000"
    },
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created resource object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "gift_cards",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/gift_cards/xYZkjABcde"
    },
    "attributes": {
      "status": "active",
      "code": "32db311a-75d9-4c17-9e34-2be220137ad6",
      "currency_code": "EUR",
      "initial_balance_cents": "15000",
      "initial_balance_float": "150.0",
      "formatted_initial_balance": "€150,00",
      "balance_cents": "15000",
      "balance_float": "150.0",
      "formatted_balance": "€150,00",
      "balance_max_cents": "100000",
      "balance_max_float": "1000.0",
      "formatted_balance_max": "€1000,00",
      "balance_log": [
        {
          "date": "2019-12-23T12:00:00.000Z",
          "amount_cents": -10000
        },
        {
          "date": "2020-02-01T12:00:00.000Z",
          "amount_cents": 5000
        }
      ],
      "single_use": "false",
      "rechargeable": "true",
      "image_url": "https://img.yourdomain.com/gift_cards/32db311a.png",
      "expires_at": "2018-01-01T12:00:00.000Z",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "recipient_email": "john@example.com",
      "_balance_change_cents": "-5000",
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
          "self": "https://yourdomain.commercelayer.io/api/gift_cards/xYZkjABcde/relationships/market",
          "related": "https://yourdomain.commercelayer.io/api/gift_cards/xYZkjABcde/market"
        }
      },
      "gift_card_recipient": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/gift_cards/xYZkjABcde/relationships/gift_card_recipient",
          "related": "https://yourdomain.commercelayer.io/api/gift_cards/xYZkjABcde/gift_card_recipient"
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
