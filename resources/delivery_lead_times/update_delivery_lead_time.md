---
description: How to update an existing delivery lead time via API
---

# Update a delivery lead time

To update an existing delivery lead time, send a `PATCH` request to the `/api/delivery_lead_times/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/delivery_lead_times/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**min_hours** | `integer` | Required |
| attributes.**max_hours** | `integer` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**stock_location** | `object` | Required |
| relationships.**shipping_method** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the delivery lead time identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/delivery_lead_times/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "delivery_lead_times",
    "id": "xYZkjABcde",
    "attributes": {
      "min_hours": "48"
      "max_hours": "72"
      "reference": "ANYREFEFERNCE"
      "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
      "stock_location": {
        "data": {
          "type": "stock_locations",
          "id": "QWERtyUpBa"
        }
      }
      "shipping_method": {
        "data": {
          "type": "shipping_methods",
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
    "type": "delivery_lead_times",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/delivery_lead_times/xYZkjABcde"
    },
    "attributes": {
        "min_hours": "48"
        "max_hours": "72"
        "min_days": "2"
        "max_days": "3"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
        "stock_location": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/delivery_lead_times/xYZkjABcde/relationships/stock_location",
              "related": "https://yourdomain.commercelayer.io/api/delivery_lead_times/xYZkjABcde/stock_location"
          }
        }
        "shipping_method": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/delivery_lead_times/xYZkjABcde/relationships/shipping_method",
              "related": "https://yourdomain.commercelayer.io/api/delivery_lead_times/xYZkjABcde/shipping_method"
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