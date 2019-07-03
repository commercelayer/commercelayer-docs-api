---
description: How to fetch a specific shipment via API
---

# Retrieve a shipment

To fetch a single shipment, send a `GET` request to the `/api/shipments/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/shipments/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the shipment identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/shipments/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a single resource object:

```javascript
{
  "data": {
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
  }
}
```
{% endtab %}
{% endtabs %}
