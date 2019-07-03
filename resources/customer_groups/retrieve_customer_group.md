---
description: How to fetch a specific customer group via API
---

# Retrieve a customer group

To fetch a single customer group, send a `GET` request to the `/api/customer_groups/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://yourdomain.commercelayer.io**/api/customer_groups/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the customer group identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/customer_groups/xYZkjABcde \
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
    "type": "customer_groups",
    "links": {
      "self": "https://yourdomein.commercelayer.io/api/customer_groups/xYZkjABcde"
    },
    "attributes": {
      "name": ""
      "created_at": "2018-01-01T12:00:00.000Z"
      "updated_at": "2018-01-01T12:00:00.000Z"
      "reference": "ANYREFEFERNCE"
      "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
      "price_list": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/customer_groups/xYZkjABcde/relationships/price_list",
            "related": "https://yourdomain.commercelayer.io/api/customer_groups/xYZkjABcde/price_list"
        }
      }
      "customers": {
        "links": {
            "self": "https://yourdomain.commercelayer.io/api/customer_groups/xYZkjABcde/relationships/customers",
            "related": "https://yourdomain.commercelayer.io/api/customer_groups/xYZkjABcde/customers"
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
