---
description: How to update an existing price list via API
---

# Update a price list

To update an existing price list, send a `PATCH` request to the `/api/price_lists/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/price_lists/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**currency_code** | `string` | Required |
| attributes.**tax_included** | `boolean` | Optional, default is 'true' |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the price list identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/price_lists/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "price_lists",
    "id": "xYZkjABcde",
    "attributes": {
      "name": "EU Price list"
    },
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning the updated resource object:

```javascript
{
  "data": {
    "id": "xYZkjABcde",
    "type": "price_lists",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/price_lists/xYZkjABcde"
    },
    "attributes": {
      "name": "EU Price list",
      "currency_code": "EUR",
      "tax_included": "true",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANYREFEFERNCE",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "prices": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/price_lists/xYZkjABcde/relationships/prices",
          "related": "https://yourdomain.commercelayer.io/api/price_lists/xYZkjABcde/prices"
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
