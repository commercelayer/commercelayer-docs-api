---
description: How to fetch a collection of customer subscriptions via API
---

# List all customer subscriptions

To fetch a collection of customer subscriptions, send a `GET` request to the `/api/customer_subscriptions` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/customer_subscriptions**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of customer subscriptions:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/customer_subscriptions/ \
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
      "id": "{{customer_subscription_id}}",
      "type": "customer_subscriptions",
      "links": {
        "self": "https://{{subdomain}}.commercelayer.io/api/customer_subscriptions/{{customer_subscription_id}}"
      },
      "attributes": {
        "customer_email": null,
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANYREFEFERNCE",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "customer": {
          "links": {
            "self": "https://{{subdomain}}.commercelayer.io/api/customer_subscriptions/{{customer_subscription_id}}/relationships/customer",
            "related": "https://{{subdomain}}.commercelayer.io/api/customer_subscriptions/{{customer_subscription_id}}/customer"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 customer_subscriptions (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://{{subdomain}}.commercelayer.io/api/customer_subscriptions?page[number]=1&page[size]=10",
    "next": "https://{{subdomain}}.commercelayer.io/api/customer_subscriptions?page[number]=2&page[size]=10",
    "last": "https://{{subdomain}}.commercelayer.io/api/customer_subscriptions?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of customer subscriptions can be sorted by the following attributes:

* `id`
* `created_at`
* `updated_at`
* `reference`

{% page-ref page="../../sorting-results.md" %}
