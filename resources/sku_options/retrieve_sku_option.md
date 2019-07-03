---
description: How to fetch a specific sku option via API
---

# Retrieve a sku option

To fetch a single sku option, send a `GET` request to the `/api/sku_options/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/sku\_options/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the sku option identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/sku_options/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

```javascript
{
  "data": {
    "name": "Embossing",
    "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
    "price_amount_cents": "1000",
    "price_amount_float": "10.00",
    "formatted_price_amount": "€10,00",
    "delay_hours": "48",
    "delay_days": "2",
    "sku_code_regex": "^(A|B).*$",
    "created_at": "2018-01-01T12:00:00.000Z",
    "updated_at": "2018-01-01T12:00:00.000Z",
    "reference": "ANYREFEFERNCE",
    "metadata": {
      "foo": "bar"
    }
  }
}
```
{% endtab %}
{% endtabs %}

