---
description: How to fetch a specific adjustment via API
---

# Retrieve an adjustment

To fetch a single adjustment, send a `GET` request to the `/api/adjustments/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/adjustments/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the adjustment identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/adjustments/xYZkjABcde \
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
    "type": "adjustments",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/adjustments/xYZkjABcde"
    },
    "attributes": {
      "name": "Additional service",
      "currency_code": "EUR",
      "amount_cents": "1500",
      "amount_float": "15.0",
      "formatted_amount": "€15,00",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {},
    "meta": {
      "mode": "test"
    }
  }
}
```
{% endtab %}
{% endtabs %}

