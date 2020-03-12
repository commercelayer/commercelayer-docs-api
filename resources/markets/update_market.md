---
description: How to update an existing market via API
---

# Update a market

To update an existing market, send a `PATCH` request to the `/api/markets/:id` endpoint, where `id` is the ID of the resource that you want to update.

Here below the list of all the possible arguments that you can pass with the request body.

{% page-ref page="../../updating-resources.md" %}

## Request

**PATCH** https://yourdomain.commercelayer.io**/api/markets/:id**

### Arguments

| Body Parameter | Type | Required |
| :--- | :--- | :--- |
| **type** | `string` | Required |
| **id** | `string` | Required |
| attributes.**name** | `string` | Optional |
| attributes.**facebook\_pixel\_id** | `string` | Optional |
| attributes.**checkout\_url** | `string` | Optional |
| attributes.**reference** | `string` | Optional |
| attributes.**reference\_origin** | `string` | Optional |
| attributes.**metadata** | `object` | Optional |
| relationships.**merchant** | `object` | Optional |
| relationships.**price\_list** | `object` | Optional |
| relationships.**inventory\_model** | `object` | Optional |
| relationships.**customer\_group** | `object` | Optional |

### Example

{% tabs %}
{% tab title="Request" %}
The following request updates the market identified by the ID "xYZkjABcde":

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/markets/xYZkjABcde \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "markets",
    "id": "xYZkjABcde",
    "attributes": {
      "name": "EU Market"
    },
    "relationships": {
      "merchant": {
        "data": {
          "type": "merchants",
          "id": "QWERtyUpBa"
        }
      },
      "price_list": {
        "data": {
          "type": "price_lists",
          "id": "QWERtyUpBa"
        }
      },
      "inventory_model": {
        "data": {
          "type": "inventory_models",
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
    "type": "markets",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde"
    },
    "attributes": {
      "number": 1234,
      "name": "EU Market",
      "facebook_pixel_id": "1234567890",
      "checkout_url": "https://checkout.yourbrand.com/:order_id",
      "private": "true",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "merchant": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/relationships/merchant",
          "related": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/merchant"
        }
      },
      "price_list": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/relationships/price_list",
          "related": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/price_list"
        }
      },
      "inventory_model": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/relationships/inventory_model",
          "related": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/inventory_model"
        }
      },
      "customer_group": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/relationships/customer_group",
          "related": "https://yourdomain.commercelayer.io/api/markets/xYZkjABcde/customer_group"
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

