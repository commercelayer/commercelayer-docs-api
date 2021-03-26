---
description: How to update an existing adyen gateway via API
---

# Update an adyen gateway

To update an existing adyen gateway, send a `PATCH` request to the `/api/adyen_gateways/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://yourdomain.commercelayer.io**/api/adyen\_gateways/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**name** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| attributes.**merchant\_account** | `string` | Optional |
| attributes.**api\_key** | `string` | Optional |
| attributes.**live\_url\_prefix** | `string` | Optional |
| relationships.**adyen\_payments** | `array` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the adyen gateway identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/adyen_gateways/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "adyen_gateways",
    "id": "xYZkjABcde",
    "attributes": {
      "reference": "ANY-EXTERNAL-REFEFERNCE"
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
    "type": "adyen_gateways",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/adyen_gateways/xYZkjABcde"
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
      "live_url_prefix": "1797a841fbb37ca7-AdyenDemo"
    },
    "relationships": {
      "payment_methods": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/adyen_gateways/xYZkjABcde/relationships/payment_methods",
          "related": "https://yourdomain.commercelayer.io/api/adyen_gateways/xYZkjABcde/payment_methods"
        }
      },
      "adyen_payments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/adyen_gateways/xYZkjABcde/relationships/adyen_payments",
          "related": "https://yourdomain.commercelayer.io/api/adyen_gateways/xYZkjABcde/adyen_payments"
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

