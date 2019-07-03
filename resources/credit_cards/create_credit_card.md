---
description: How to create a credit card via API
---

# Create a credit card

To create a new credit card, send a `POST` request to the `/api/credit_cards` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/credit_cards**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**first_name** | `string` | Required |
| attributes.**last_name** | `string` | Required |
| attributes.**number** | `string` | Required |
| attributes.**month** | `string` | Required |
| attributes.**year** | `string` | Required |
| attributes.**verification_value** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**order** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new credit card:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/credit_cards \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "credit_cards",
    "attributes": {
      "first_name": "John"
      "last_name": "Smith"
      "number": "4111111111111111"
      "month": "10"
      "year": "2023"
      "verification_value": "123"
    },
    "relationships": {
      "order": {
        "data": {
          "type": "orders",
          "id": "QWERtyUpBa"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `credit card` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "credit_cards",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/credit_cards/xYZkjABcde"
    },
    "attributes": {
      "first_name": "John",
      "last_name": "Smith",
      "full_name": "John Smith",
      "month": "10",
      "year": "2023",
      "valid_thru": "10/2023",
      "card_type": "visa",
      "display_number": "XXXX-XXXX-XXXX-1111",
      "name": "XXXX-XXXX-XXXX-1111",
      "fingerprint": "9abc5b0ef273e53749068820b3a30640b838",
      "storage_state": "cached",
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
          "self": "https://yourdomain.commercelayer.io/api/credit_cards/xYZkjABcde/relationships/order",
          "related": "https://yourdomain.commercelayer.io/api/credit_cards/xYZkjABcde/order"
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
