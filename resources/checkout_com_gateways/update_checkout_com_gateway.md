---
description: How to update an existing checkout com gateway via API
---

# Update a checkout com gateway

To update an existing checkout com gateway, send a `PATCH` request to the `/api/checkout_com_gateways/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/checkout_com_gateways/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**name** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| attributes.**secret_key** | `string` | Optional |
| attributes.**public_key** | `string` | Optional |
| relationships.**checkout_com_payments** | `array` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the checkout com gateway identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "checkout_com_gateways",
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
    "type": "checkout_com_gateways",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde"
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
      "webhook_endpoint_id": "xxxx-yyyy-zzzz",
      "webhook_endpoint_secret": "xxxx-yyyy-zzzz",
      "webhook_endpoint_url": "https://core.commercelayer.co/webhook_callbacks/checkout_com_gateways/xxxxx"
    },
    "relationships": {
      "payment_methods": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde/relationships/payment_methods",
          "related": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde/payment_methods"
        }
      },
      "checkout_com_payments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde/relationships/checkout_com_payments",
          "related": "https://yourdomain.commercelayer.io/api/checkout_com_gateways/xYZkjABcde/checkout_com_payments"
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

