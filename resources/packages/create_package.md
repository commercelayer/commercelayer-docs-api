---
description: How to create a package via API
---

# Create a package

To create a new package, send a `POST` request to the `/api/packages` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/packages**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | Optional |
| attributes.**code** | `string` | Optional |
| attributes.**length** | `float` | Optional |
| attributes.**width** | `float` | Optional |
| attributes.**height** | `float` | Optional |
| attributes.**unit_of_length** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**stock_location** | `object` | Required |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new package:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/packages \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "packages",
    "relationships": {
      "stock_location": {
        "data": {
          "type": "stock_locations",
          "id": "QWERtyUpBa"
        }
      }
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created resource object:

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
      "length": 40.0,
      "width": 40.0,
      "height": 25.0,
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
      },
      "attachments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/packages/xYZkjABcde/relationships/attachments",
          "related": "https://yourdomain.commercelayer.io/api/packages/xYZkjABcde/attachments"
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

