---
description: How to create a customer group via API
---

# Create a customer group

To create a new customer group, send a `POST` request to the `/api/customer_groups` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://yourdomain.commercelayer.io**/api/customer\_groups**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**price\_list** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new customer group:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/customer_groups \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "customer_groups",
    "attributes": {
      "name": ""
    },
    "relationships": {
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created `customer group` object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "customer_groups",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/customer_groups/xYZkjABcde"
    },
    "attributes": {
      "name": null,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "price_list": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/customer_groups/{{customer_group_id}}/relationships/price_list",
          "related": "https://{{subdomain}}.commercelayer.io/api/customer_groups/{{customer_group_id}}/price_list"
        }
      },
      "customers": {
        "links": {
          "self": "https://{{subdomain}}.commercelayer.io/api/customer_groups/{{customer_group_id}}/relationships/customers",
          "related": "https://{{subdomain}}.commercelayer.io/api/customer_groups/{{customer_group_id}}/customers"
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

