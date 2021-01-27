---
description: How to fetch a specific parcel line item via API
---

# Retrieve a parcel line item

To fetch a single parcel line item, send a `GET` request to the `/api/parcel_line_items/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/parcel\_line\_items/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the parcel line item identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/parcel_line_items/xYZkjABcde \
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
    "type": "parcel_line_items",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/parcel_line_items/xYZkjABcde"
    },
    "attributes": {
      "sku_code": "TSHIRTMM000000FFFFFFXLXX",
      "quantity": null,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "parcel": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/parcel_line_items/xYZkjABcde/relationships/parcel",
          "related": "https://yourdomain.commercelayer.io/api/parcel_line_items/xYZkjABcde/parcel"
        }
      },
      "shipment_line_item": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/parcel_line_items/xYZkjABcde/relationships/shipment_line_item",
          "related": "https://yourdomain.commercelayer.io/api/parcel_line_items/xYZkjABcde/shipment_line_item"
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

