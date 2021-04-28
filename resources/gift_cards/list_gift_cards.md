---
description: How to fetch a collection of gift cards via API
---

# List all gift cards

To fetch a collection of gift cards, send a `GET` request to the `/api/gift_cards` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/gift\_cards**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of gift cards:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/gift_cards/ \
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
      "type": "gift_cards",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/gift_cards/xYZkjABcde"
      },
      "attributes": {
        "status": "draft",
        "code": "32db311a-75d9-4c17-9e34-2be220137ad6",
        "currency_code": "EUR",
        "initial_balance_cents": 15000,
        "initial_balance_float": 150.0,
        "formatted_initial_balance": "€150,00",
        "balance_cents": 15000,
        "balance_float": 150.0,
        "formatted_balance": "€150,00",
        "balance_max_cents": "100000",
        "balance_max_float": 1000.0,
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
        "single_use": false,
        "rechargeable": true,
        "image_url": "https://img.yourdomain.com/gift_cards/32db311a.png",
        "expires_at": "2018-01-01T12:00:00.000Z",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "recipient_email": "john@example.com",
        "_balance_change_cents": -5000,
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
        },
        "attachments": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/gift_cards/xYZkjABcde/relationships/attachments",
            "related": "https://yourdomain.commercelayer.io/api/gift_cards/xYZkjABcde/attachments"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 gift_cards (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/gift_cards?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/gift_cards?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/gift_cards?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of gift cards can be sorted by the following attributes:

* `currency_code`
* `balance_cents`
* `balance_max_cents`
* `expires_at`
* `reference_origin`
* `id`
* `created_at`
* `updated_at`
* `reference`

{% page-ref page="../../sorting-results.md" %}

