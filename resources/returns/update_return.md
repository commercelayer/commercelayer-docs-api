---
description: How to update an existing return via API
---

# Update a return

To update an existing return, send a `PATCH` request to the `/api/returns/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/returns/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**_request** | `boolean, value is 'true'` | Optional |
| attributes.**_approve** | `boolean, value is 'true'` | Optional |
| attributes.**_reject** | `boolean, value is 'true'` | Optional |
| attributes.**_ship** | `boolean, value is 'true'` | Optional |
| attributes.**_receive** | `boolean, value is 'true'` | Optional |
| attributes.**_restock** | `boolean, value is 'true'` | Optional |
| attributes.**_archive** | `boolean, value is 'true'` | Optional |
| attributes.**_unarchive** | `boolean, value is 'true'` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**stock_location** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the return identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/returns/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "returns",
    "id": "xYZkjABcde",
    "attributes": {
      "_request": "true"
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

