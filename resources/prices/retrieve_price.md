---
description: How to fetch a specific price via API
---

# Retrieve a price

To fetch a single price, send a `GET` request to the `/api/prices/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/prices/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the price identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/prices/xYZkjABcde \
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
    "type": "prices",
    "links": {
      "self": "https://yourdomein.commercelayer.io/api/prices/xYZkjABcde"
    },
    "attributes": {
      "currency_code": "EUR",
      "sku_code": "TSHIRTMM000000FFFFFFXLXX",
      "amount_cents": "10000",
      "amount_float": "100.0",
      "formatted_amount": "€100,00",
      "compare_at_amount_cents": "13000",
      "compare_at_amount_float": "130.00",
      "formatted_compare_at_amount": "€130,00",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
                "foo": "bar"
              },
    },
    "relationships": {
      "price_list": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde/relationships/price_list",
            "related": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde/price_list"
        }
      },
      "sku": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde/relationships/sku",
            "related": "https://yourdomain.commercelayer.io/api/prices/xYZkjABcde/sku"
        }
      },
    },
    "meta": {
      "mode": "test"
    }
  }
}
```
{% endtab %}
{% endtabs %}
