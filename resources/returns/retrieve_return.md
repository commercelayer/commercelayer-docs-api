---
description: How to fetch a specific return via API
---

# Retrieve a return

To fetch a single return, send a `GET` request to the `/api/returns/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/returns/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the return identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/returns/xYZkjABcde \
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
    "type": "returns",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde"
    },
    "attributes": {
      "number": "#1234/R/001",
      "status": "draft",
      "customer_email": "john@example.com",
      "skus_count": "2",
      "approved_at": "2018-01-01T12:00:00.000Z",
      "rejected_at": "2018-01-01T12:00:00.000Z",
      "shipped_at": "2018-01-01T12:00:00.000Z",
      "received_at": "2018-01-01T12:00:00.000Z",
      "archived_at": "2018-01-01T12:00:00.000Z",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "order": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/relationships/order",
          "related": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/order"
        }
      },
      "customer": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/relationships/customer",
          "related": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/customer"
        }
      },
      "inventory_return_location": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/relationships/inventory_return_location",
          "related": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/inventory_return_location"
        }
      },
      "stock_location": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/relationships/stock_location",
          "related": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/stock_location"
        }
      },
      "origin_address": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/relationships/origin_address",
          "related": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/origin_address"
        }
      },
      "destination_address": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/relationships/destination_address",
          "related": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/destination_address"
        }
      },
      "return_line_items": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/relationships/return_line_items",
          "related": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/return_line_items"
        }
      },
      "attachments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/relationships/attachments",
          "related": "https://yourdomain.commercelayer.io/api/returns/xYZkjABcde/attachments"
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

