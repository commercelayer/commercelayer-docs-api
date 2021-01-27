---
description: How to fetch a collection of packages via API
---

# List all packages

To fetch a collection of packages, send a `GET` request to the `/api/packages` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/packages**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of packages:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/packages/ \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning a paginated collection of resource objects:

```javascript
{
  "data": [
    {
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
    },
    {
      "other": "... 9 packages (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/packages?page[number]=1&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/packages?page[number]=2&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/packages?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

{% page-ref page="../../pagination.md" %}

### Sortable attributes

The list of packages can be sorted by the following attributes:

* `name`
* `id`
* `created_at`
* `updated_at`
* `reference`
* `reference_origin`

{% page-ref page="../../sorting-results.md" %}

