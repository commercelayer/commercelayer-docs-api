---
description: How to fetch a collection of customers via API
---

# List all customers

To fetch a collection of customers, send a `GET` request to the `/api/customers` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/customers**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of customers:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/customers/ \
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
      "email": "john@example.com",
      "status": "prospect",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    {
      "other": "... 9 customers (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/customers?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/customers?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/customers?page[number]=14&page[size]=10"
  }
}


{
  "data": [
    {
      "id": "xYZkjABcde",
      "type": "customers",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde"
      },
      "attributes": {
        "email": "john@example.com",
        "status": "prospect",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANYREFEFERNCE",
        "metadata": {
  "foo": "bar"
},
      },
      "relationships": {
        "customer_group": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/relationships/customer_group",
              "related": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/customer_group"
          }
        },
        "customer_addresses": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/relationships/customer_addresses",
              "related": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/customer_addresses"
          }
        },
        "customer_payment_sources": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/relationships/customer_payment_sources",
              "related": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/customer_payment_sources"
          }
        },
        "customer_subscriptions": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/relationships/customer_subscriptions",
              "related": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/customer_subscriptions"
          }
        },
        "orders": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/relationships/orders",
              "related": "https://yourdomain.commercelayer.io/api/customers/xYZkjABcde/orders"
          }
        },
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 customers (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/customers?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/customers?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/customers?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of customers can be sorted by the following attributes:

* `id`
* `created_at`
* `updated_at`
* `reference`

{% page-ref page="../../sorting-results.md" %}

