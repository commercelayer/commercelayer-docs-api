---
description: How to fetch a specific customer address via API
---

# Retrieve a customer address

To fetch a single customer address, send a `GET` request to the `/api/customer_addresses/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/customer_addresses/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the customer address identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/customer_addresses/xYZkjABcde \
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
    "type": "customer_addresses",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/customer_addresses/xYZkjABcde"
    },
    "attributes": {
      "name": "John Smith, 2883 Geraldine Lane Apt.23, 10013 New York NY (US) (212) 646-338-1228",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "customer": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/customer_addresses/xYZkjABcde/relationships/customer",
          "related": "https://yourdomain.commercelayer.io/api/customer_addresses/xYZkjABcde/customer"
        }
      },
      "address": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/customer_addresses/xYZkjABcde/relationships/address",
          "related": "https://yourdomain.commercelayer.io/api/customer_addresses/xYZkjABcde/address"
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

