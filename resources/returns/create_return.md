---
description: How to create a return via API
---

# Create a return

To create a new return, send a `POST` request to the `/api/returns` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/returns**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**order** | `object` | Required |
| relationships.**stock_location** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new return:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/returns \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "returns",
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
On success, the API responds with a `201 Created` status code, returning the created resource object:

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
      "skus_count": 2,
      "approved_at": "2018-01-01T12:00:00.000Z",
      "cancelled_at": "2018-01-01T12:00:00.000Z",
      "shipped_at": "2018-01-01T12:00:00.000Z",
      "rejected_at": "2018-01-01T12:00:00.000Z",
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

