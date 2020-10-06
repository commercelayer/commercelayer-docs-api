---
description: How to manage prices via serverless functions
---

# External prices

You can decide not to manage your product prices within Commerce Layer and use an external service of your choice \(or build your own\) to take advantage of any price calculation logic you need for your business. 

All we require is the URL of the endpoint that will calculate the unit price of the SKU when it's added to an order and the related line item is created. You can set the `external_price_url` by filling the related field when you create/edit a market. 

{% page-ref page="../resources/markets/" %}

{% hint style="info" %}
If the `external_price_url` field is not empty, having a price defined in one of the market price lists is no more mandatory for an SKU to be _sellable_ in that specific market.
{% endhint %}

###  Invoking the external price calculation for an SKU

If an application has in scope a market where the `external_price_url` is set, when a line item of type `skus` is added to an order you can require the unit price to be calculated by your external service at the moment of the related line item creation. 

{% page-ref page="../resources/line\_items/create\_line\_item.md" %}

To do that and trigger a `POST` request to the external price endpoint, just specify the `sku_code` and set the `_external_price` attribute to `true`:

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
      "quantity": "2",
      "sku_code": "TSHIRTMM000000FFFFFFXLXX",
      "_external_price": "true"
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

### Example

{% tabs %}
{% tab title="Payload" %}
The request payload contains the line item and includes the associated order:

```javascript
{
  data: {
    id: 'xYZkjABcde',
    type: 'line_items',
    links: { ... },
    attributes: { ... },
    relationships: { ... },
    meta: { ... }
  },
  included: [
    {
      id: 'wBXVhKzrnq',
      type: 'orders',
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
  "success": "true",
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
  "success": "false",
  "error": {
    "code": "YOUR-ERROR-CODE",
    "message": "Your error message"
  }
}
```
{% endtab %}
{% endtabs %}

#### 



