---
description: How to fetch a specific coupon via API
---

# Retrieve a coupon

To fetch a single coupon, send a `GET` request to the `/api/coupons/:id` endpoint, where `id` is the ID of the resource that you want to retrieve.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/coupons/:id**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the coupon identified by the id "xYZkjABcde":

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/coupons/xYZkjABcde \
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
    "type": "coupons",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/coupons/xYZkjABcde"
    },
    "attributes": {
      "code": "04371af2-70b3-48d7-8f4e-316b374224c3",
      "usage_limit": 50,
      "usage_count": 20,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {
      "promotion_rule": {
        "links": {
          "self": "https://yourdomain.commercelayer.io/api/coupons/xYZkjABcde/relationships/promotion_rule",
          "related": "https://yourdomain.commercelayer.io/api/coupons/xYZkjABcde/promotion_rule"
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

