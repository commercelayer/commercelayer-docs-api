---
description: How to fetch the organization via API
---

# Retrieve the organization

To fetch the organization, send a `GET` request to the `/api/organizations` endpoint.

{% page-ref page="../../fetching-resources.md" %}

## Request

**GET** https://<i></i>yourdomain.commercelayer.io**/api/organizations**

### **Example**

{% tabs %}
{% tab title="Request" %}
The following request fetches the organization in scope:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/organizations/ \
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
    "type": "organizations",
    "links": {
      "self": "https://yourdomain.commercelayer.io/api/organizations/xYZkjABcde"
    },
    "attributes": {
      "name": "The Blue Brand",
      "slug": "the-blue-brand",
      "domain": "the-blue-brand.commercelayer.io",
      "logo_url": "https://bluebrand.com/img/logo.svg",
      "favicon_url": "https://bluebrand.com/img/favicon.ico",
      "primary_color": "#C8984E",
      "ga_property_id": "UA-10876-1",
      "ga_property_id_test": "UA-10876-1",
      "discount_disabled": "false",
      "account_disabled": "false",
      "acceptance_disabled": "false",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": "ANY-EXTERNAL-REFEFERNCE",
      "reference_origin": "ANY-EXTERNAL-REFEFERNCE-ORIGIN",
      "metadata": {
        "foo": "bar"
      }
    },
    "relationships": {},
    "meta": {
      "mode": "test"
    }
  }
}
```
{% endtab %}
{% endtabs %}

