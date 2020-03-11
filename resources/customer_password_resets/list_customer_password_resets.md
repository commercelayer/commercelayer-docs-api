---
description: How to fetch a collection of customer password resets via API
---

# List all customer password resets

To fetch a collection of customer password resets, send a `GET` request to the `/api/customer_password_resets` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/customer_password_resets**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of customer password resets:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/customer_password_resets/ \
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
      "type": "customer_password_resets",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/customer_password_resets/xYZkjABcde"
      },
      "attributes": {
        "customer_email": "john@example.com",
        "reset_password_token": "xhFfkmfybsLxzaAP6xcs",
        "reset_password_at": "2018-01-01T12:00:00.000Z",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANY-EXTERNAL-REFEFERNCE",
        "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "customer": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/customer_password_resets/xYZkjABcde/relationships/customer",
            "related": "https://yourdomain.commercelayer.io/api/customer_password_resets/xYZkjABcde/customer"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 customer_password_resets (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/customer_password_resets?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/customer_password_resets?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/customer_password_resets?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of customer password resets can be sorted by the following attributes:

* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}
