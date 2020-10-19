---
description: How to fetch a specific shipping method via API
---

# Retrieve a shipping method

To fetch a single shipping method, send a `GET` request to the `/api/shipping_methods/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/shipping_methods/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the shipping method identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde \
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
    "type": "shipping_methods",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde"
    },
    "attributes": {
      "name": "Standard shipping",
      "disabled_at": "2018-01-01T12:00:00.000Z",
      "currency_code": "EUR",
      "price_amount_cents": "1000",
      "price_amount_float": "10.00",
      "formatted_price_amount": "€10,00",
      "free_over_amount_cents": "9900",
      "free_over_amount_float": "99.00",
      "formatted_free_over_amount": "€99,00",
      "price_amount_for_shipment_cents": "0",
      "price_amount_for_shipment_float": "0.0",
      "formatted_price_amount_for_shipment": "€0,00",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "market": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/relationships/market",
          "related": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/market"
        }
      },
      "shipping_zone": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/relationships/shipping_zone",
          "related": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/shipping_zone"
        }
      },
      "shipping_category": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/relationships/shipping_category",
          "related": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/shipping_category"
        }
      },
      "delivery_lead_time_for_shipment": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/relationships/delivery_lead_time_for_shipment",
          "related": "https://yourdomain.commercelayer.io/api/shipping_methods/xYZkjABcde/delivery_lead_time_for_shipment"
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

