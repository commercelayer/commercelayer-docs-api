---
description: How to fetch a collection of credit cards via API
---

# List all credit cards

To fetch a collection of credit cards, send a `GET` request to the `/api/credit_cards` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/credit_cards**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of credit cards:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/credit_cards/ \
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
    },
    {
      "other": "... 9 credit_cards (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/credit_cards?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/credit_cards?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/credit_cards?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of credit cards can be sorted by the following attributes:

* `card_type`
* `id`
* `created_at`
* `updated_at`
* `reference`

{% page-ref page="../../sorting-results.md" %}
