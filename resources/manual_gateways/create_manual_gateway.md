---
description: How to create a manual gateway via API
---

# Create a manual gateway

To create a new manual gateway, send a `POST` request to the `/api/manual_gateways` endpoint, passing the resource arguments in the request body.

{% page-ref page="../../creating-resources.md" %}

## Request

**POST** https://<i></i>yourdomain.commercelayer.io**/api/manual_gateways**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| attributes.**name** | `string` | Required |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| attributes.**require_capture** | `boolean` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request creates a new manual gateway:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/manual_gateways \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "manual_gateways",
    "attributes": {
      "name": "US payment gateway"
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
    "type": "manual_gateways",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/manual_gateways/xYZkjABcde"
    },
    "attributes": {
      "name": "US payment gateway",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      },
      "require_capture": true
    },
    "relationships": {
      "payment_methods": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/manual_gateways/xYZkjABcde/relationships/payment_methods",
          "related": "https://yourdomain.commercelayer.io/api/manual_gateways/xYZkjABcde/payment_methods"
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

