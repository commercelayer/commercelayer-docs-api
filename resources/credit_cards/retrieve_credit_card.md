---
description: How to fetch a specific credit card via API
---

# Retrieve a credit card

To fetch a single credit card, send a `GET` request to the `/api/credit_cards/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/credit\_cards/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the credit card identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/credit_cards/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "credit_cards",
    "links": {
      "self": "https://yourdomein.commercelayer.io/api/credit_cards/xYZkjABcde"
    },
    "attributes": {
      "first_name": "John"
      "last_name": "Smith"
      "full_name": "John Smith"
      "month": "10"
      "year": "2023"
      "valid_thru": "10/2023"
      "card_type": "visa"
      "display_number": "XXXX-XXXX-XXXX-1111"
      "name": "XXXX-XXXX-XXXX-1111"
      "fingerprint": "9abc5b0ef273e53749068820b3a30640b838"
      "storage_state": "cached"
      "created_at": "2018-01-01T12:00:00.000Z"
      "updated_at": "2018-01-01T12:00:00.000Z"
      "reference": "ANYREFEFERNCE"
      "metadata": "{:foo=>"bar"}"
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

