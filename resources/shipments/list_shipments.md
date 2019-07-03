---
description: How to fetch a collection of shipments via API
---

# List all shipments

To fetch a collection of shipments, send a `GET` request to the `/api/shipments` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/shipments**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of shipments:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/shipments/ \
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
      "id": "{{shipment_id}}",
      "type": "shipments",
      "links": {
        "self": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}"
      },
      "attributes": {
        "number": "#1234/S/001",
        "status": "draft",
        "currency_code": "EUR",
        "cost_amount_cents": "1000",
        "cost_amount_float": "10.00",
        "formatted_cost_amount": "€10,00",
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANYREFEFERNCE",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "shipping_category": {
          "links": {
            "self": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/relationships/shipping_category",
            "related": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/shipping_category"
          }
        },
        "stock_location": {
          "links": {
            "self": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/relationships/stock_location",
            "related": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/stock_location"
          }
        },
        "shipping_address": {
          "links": {
            "self": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/relationships/shipping_address",
            "related": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/shipping_address"
          }
        },
        "shipping_method": {
          "links": {
            "self": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/relationships/shipping_method",
            "related": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/shipping_method"
          }
        },
        "shipment_line_items": {
          "links": {
            "self": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/relationships/shipment_line_items",
            "related": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/shipment_line_items"
          }
        },
        "available_shipping_methods": {
          "links": {
            "self": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/relationships/available_shipping_methods",
            "related": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/available_shipping_methods"
          }
        },
        "parcels": {
          "links": {
            "self": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/relationships/parcels",
            "related": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/parcels"
          }
        },
        "attachments": {
          "links": {
            "self": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/relationships/attachments",
            "related": "https://{{subdomain}}.commercelayer.io/api/shipments/{{shipment_id}}/attachments"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 shipments (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://{{subdomain}}.commercelayer.io/api/shipments?page[number]=1&page[size]=10",
    "next": "https://{{subdomain}}.commercelayer.io/api/shipments?page[number]=2&page[size]=10",
    "last": "https://{{subdomain}}.commercelayer.io/api/shipments?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of shipments can be sorted by the following attributes:

* `status`
* `id`
* `created_at`
* `updated_at`
* `reference`

{% page-ref page="../../sorting-results.md" %}
