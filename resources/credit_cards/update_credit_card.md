---
description: How to update an existing credit card via API
---

# Update a credit card

To update an existing credit card, send a `PATCH` request to the `/api/credit_cards/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/credit_cards/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**first_name** | `string` | Required |
| attributes.**last_name** | `string` | Required |
| attributes.**month** | `string` | Required |
| attributes.**year** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**order** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the credit card identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/credit_cards/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "credit_cards",
    "id": "xYZkjABcde",
    "attributes": {
      "first_name": "John"
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
On success, the API responds with a `200 OK` status code, returning the updated resource object:

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
      "reference": "ANY-EXTERNAL-REFEFERNCE",
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
