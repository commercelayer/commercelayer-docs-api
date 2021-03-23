---
description: How to fetch a specific package via API
---

# Retrieve a package

To fetch a single package, send a `GET` request to the `/api/packages/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/packages/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the package identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/packages/xYZkjABcde \
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

