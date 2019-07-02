---
description: How to create A delivery lead time via API
---

# Create A delivery lead time

To create a new delivery lead time, send a `POST` request to the `/api/delivery_lead_times` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/delivery_lead_times**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**min_hours** | `integer` | required |
| attributes.**max_hours** | `integer` | required |
| attributes.**min_days** | `integer` |  |
| attributes.**max_days** | `integer` |  |
| attributes.**id** | `string` | required |
| attributes.**created_at** | `datetime` | required |
| attributes.**updated_at** | `datetime` | required |
| attributes.**reference** | `string` | optional |
| attributes.**metadata** | `object` | optional |
| relationships.**stock_location** | `has_one` | required |
| relationships.**shipping_method** | `has_one` | required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new delivery lead time:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/delivery_lead_times \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "delivery_lead_times",
    "attributes": {
      "min_hours": "48"
      "max_hours": "72"
    },
    "relationships": {
      "stock_location": {
        "data": {
          "type": "stock_locations",
          "id": "zxcVBnMASd"
        }
      }
      "shipping_method": {
        "data": {
          "type": "shipping_methods",
          "id": "zxcVBnMASd"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `delivery lead time` object:

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
