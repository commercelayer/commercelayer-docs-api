---
description: How to manage prices via external services
---

# External prices

Sometimes, you can decide not to manage prices within Commerce Layer but use an external service instead. The reason can be to support more dynamic pricing or just leverage an existing service that you want to keep as your system of records.

If you want to support external prices in a market, fill in the market's `external_price_url` field with your external service endpoint and make sure your service supports the specification described below.

### Fetching external prices

When you add a line item to an order, set the `_external_price` attribute to `true` if you want the line item price to be provided by your external service, instead of Commerce Layer:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/line_items \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
  "data": {
    "type": "line_items",
    "attributes": {
      "quantity": 2,
      "sku_code": "TSHIRTMM000000FFFFFFXLXX",
      "_external_price": true
    },
    "relationships": {
      "order": {
        "data": {
          "type": "orders",
          "id": "QWERtyUpBa"
        }
      }
    }
  }
}'
```

Upon line item creation, Commerce Layer triggers a `POST` request to the specified `external_price_url` endpoint, sending the line item payload \(including the order\) in the request body. Your service response \(or error\) must match the format described in the example below.

### Example

{% tabs %}
{% tab title="Payload" %}
The request payload contains the line item and includes the associated order:

```javascript
{
  data: {
    id: "xYZkjABcde",
    type: "line_items",
    links: { ... },
    attributes: {
      "quantity": 2,
      "sku_code": "TSHIRTMM000000FFFFFFXLXX",
      "_external_price": true
    },
    relationships: { ... },
    meta: { ... }
  },
  included: [
    {
      id: "wBXVhKzrnq",
      type: "orders",
      links: { ... },
      attributes: { ... },
      relationships: { ... },
      meta: { ... }
    }
  ]
}
```
{% endtab %}

{% tab title="Response" %}
The successful response must be a JSON object, returning the unit price computed by the external logic and the SKU code of the related product, along with some additional information and metadata:

```javascript
{
  "success": true,
  "data": {
    "sku_code": "TSHIRTMM000000FFFFFFXLXX",
    "unit_amount_cents": 4900,
    "metadata": {
      "foo": "bar"
    }
  }
}
```
{% endtab %}

{% tab title="Error" %}
On error, the response must be a JSON object containing an error code and an error message:

```javascript
{
  "success": false,
  "error": {
    "code": "YOUR-ERROR-CODE",
    "message": "Your error message"
  }
}
```
{% endtab %}
{% endtabs %}

### SKUs availability

When you fetch a list of SKUs with a sales channel application, you only get those SKUs that have a price defined in the market's price list and at least a stock item in one of the market stock locations. 

{% hint style="info" %}
In case you manage prices externally, the price filter is not considered.
{% endhint %}

### Security

When you activate external prices support for a market, a **shared secret** is generated. We recommend verifying the callback authenticity by signing the payload with that shared secret and comparing the result with the callback signature header.

{% page-ref page="../callbacks-security.md" %}

