---
description: How to update an existing braintree gateway via API
---

# Update a braintree gateway

To update an existing braintree gateway, send a `PATCH` request to the `/api/braintree_gateways/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://<i></i>yourdomain.commercelayer.io**/api/braintree_gateways/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**name** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| attributes.**merchant_account_id** | `string` | Optional |
| attributes.**merchant_id** | `string` | Optional |
| attributes.**public_key** | `string` | Optional |
| attributes.**private_key** | `string` | Optional |
| attributes.**descriptor_name** | `string` | Optional |
| attributes.**descriptor_phone** | `string` | Optional |
| attributes.**descriptor_url** | `string` | Optional |
| relationships.**braintree_payments** | `array` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the braintree gateway identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/braintree_gateways/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "braintree_gateways",
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
    "type": "braintree_gateways",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/braintree_gateways/xYZkjABcde"
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
      "descriptor_name": "company*productabc1234",
      "descriptor_phone": "3125551212",
      "descriptor_url": "company.com",
      "webhook_endpoint_url": "https://core.commercelayer.co/webhook_callbacks/braintree_gateways/xxxxx"
    },
    "relationships": {
      "payment_methods": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/braintree_gateways/xYZkjABcde/relationships/payment_methods",
          "related": "https://yourdomain.commercelayer.io/api/braintree_gateways/xYZkjABcde/payment_methods"
        }
      },
      "braintree_payments": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/braintree_gateways/xYZkjABcde/relationships/braintree_payments",
          "related": "https://yourdomain.commercelayer.io/api/braintree_gateways/xYZkjABcde/braintree_payments"
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

