---
description: How to create a delivery lead time via API
---

# Create a delivery lead time

To create a new delivery lead time, send a `POST` request to the `/api/delivery_lead_times` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/delivery_lead_times**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**min_hours** | `integer` | Required |
| attributes.**max_hours** | `integer` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**stock_location** | `object` | Required |
| relationships.**shipping_method** | `object` | Required |

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
On success, the API responds with a `201 Created` status code, returning the created `delivery lead time` object:

```javascript
{
  "data": {
    "id": "{{delivery_lead_time_id}}",
    "type": "delivery_lead_times",
    "links": {
      "self": "https://{{subdomain}}.commercelayer.io/api/delivery_lead_times/{{delivery_lead_time_id}}"
    },
    "attributes": {
      "min_hours": "48",
      "max_hours": "72",
      "min_days": "2",
      "max_days": "3",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "stock_location": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/delivery_lead_times/{{delivery_lead_time_id}}/relationships/stock_location",
          "related": "https://{{subdomain}}.commercelayer.io/api/delivery_lead_times/{{delivery_lead_time_id}}/stock_location"
        }
      },
      "shipping_method": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/delivery_lead_times/{{delivery_lead_time_id}}/relationships/shipping_method",
          "related": "https://{{subdomain}}.commercelayer.io/api/delivery_lead_times/{{delivery_lead_time_id}}/shipping_method"
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
