---
description: How to update an existing stock location via API
---

# Update a stock location

To update an existing stock location, send a `PATCH` request to the `/api/stock_locations/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/stock_locations/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**label_format** | `string` | Optional, default is 'pdf' |
| attributes.**reference** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**address** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the stock location identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "stock_locations",
    "id": "xYZkjABcde",
    "attributes": {
      "name": "Primary warehouse"
      "label_format": "PDF"
      "reference": "ANYREFEFERNCE"
      "metadata": "{:foo=>"bar"}"
    },
    "relationships": {
      "address": {
        "data": {
          "type": "addresses",
          "id": "QWERtyUpBa"
        }
      }
    }
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
    "type": "stock_locations",
    "links": {
        "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde"
    },
    "attributes": {
        "name": "Primary warehouse"
        "label_format": "PDF"
        "created_at": "2018-01-01T12:00:00.000Z"
        "updated_at": "2018-01-01T12:00:00.000Z"
        "reference": "ANYREFEFERNCE"
        "metadata": "{
  "foo": "bar"
}"
    },
    "relationships": {
        "address": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/address",
              "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/address"
          }
        }
        "stock_levels": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/stock_levels",
              "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/stock_levels"
          }
        }
        "stock_items": {
          "links": {
              "self": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/relationships/stock_items",
              "related": "https://yourdomain.commercelayer.io/api/stock_locations/xYZkjABcde/stock_items"
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
