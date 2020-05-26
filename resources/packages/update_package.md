---
description: How to update an existing package via API
---

# Update a package

To update an existing package, send a `PATCH` request to the `/api/packages/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/packages/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**name** | `string` | Optional |
| attributes.**code** | `string` | Optional |
| attributes.**length** | `float` | Optional |
| attributes.**width** | `float` | Optional |
| attributes.**height** | `float` | Optional |
| attributes.**unit_of_length** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**stock_location** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the package identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/packages/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "packages",
    "id": "xYZkjABcde",
    "attributes": {
      "code": "YYYY 2000"
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
    "type": "packages",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/packages/xYZkjABcde"
    },
    "attributes": {
      "name": "Large (60x40x30)",
      "code": "YYYY 2000",
      "length": "40.0",
      "width": "40.0",
      "height": "25.0",
      "unit_of_length": "gr",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "stock_location": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/packages/xYZkjABcde/relationships/stock_location",
          "related": "https://yourdomain.commercelayer.io/api/packages/xYZkjABcde/stock_location"
        }
      },
      "parcels": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/packages/xYZkjABcde/relationships/parcels",
          "related": "https://yourdomain.commercelayer.io/api/packages/xYZkjABcde/parcels"
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

