---
description: How to fetch a collection of gift card recipients via API
---

# List all gift card recipients

To fetch a collection of gift card recipients, send a `GET` request to the `/api/gift_card_recipients` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/gift_card_recipients**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of gift card recipients:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/gift_card_recipients/ \
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
      "type": "gift_card_recipients",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/gift_card_recipients/xYZkjABcde"
      },
      "attributes": {
        "email": "john@example.com",
        "first_name": "John",
        "last_name": "Smith",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "customer": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/gift_card_recipients/xYZkjABcde/relationships/customer",
            "related": "https://yourdomain.commercelayer.io/api/gift_card_recipients/xYZkjABcde/customer"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 gift_card_recipients (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/gift_card_recipients?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/gift_card_recipients?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/gift_card_recipients?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of gift card recipients can be sorted by the following attributes:

* `reference_origin`
* `id`
* `created_at`
* `updated_at`
* `reference`

{% page-ref page="../../sorting-results.md" %}

