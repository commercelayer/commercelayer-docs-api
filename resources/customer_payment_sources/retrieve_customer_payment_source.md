---
description: How to fetch a specific customer payment source via API
---

# Retrieve a customer payment source

To fetch a single customer payment source, send a `GET` request to the `/api/customer_payment_sources/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/customer_payment_sources/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the customer payment source identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/customer_payment_sources/xYZkjABcde \
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
    "type": "customer_payment_sources",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/customer_payment_sources/xYZkjABcde"
    },
    "attributes": {
      "name": "XXXX-XXXX-XXXX-1111",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "customer": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/customer_payment_sources/{{customer_payment_source_id}}/relationships/customer",
          "related": "https://{{subdomain}}.commercelayer.io/api/customer_payment_sources/{{customer_payment_source_id}}/customer"
        }
      },
      "payment_source": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/customer_payment_sources/{{customer_payment_source_id}}/relationships/payment_source",
          "related": "https://{{subdomain}}.commercelayer.io/api/customer_payment_sources/{{customer_payment_source_id}}/payment_source"
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
