---
description: How to manage custom tax calculation via external services
---

# External tax calculators

Commerce Layer supports automatic tax calculation thanks to the out-of-the-box integration with **Avalara** and **TaxJar**. Manual tax calculators can be also configured. On top of that, you also have the complete flexibility to implement any particular custom tax calculation logic building your own external tax calculator.

{% page-ref page="../resources/external\_tax\_calculators/" %}

Whenever the tax calculation is fired, Commerce Layer triggers a `POST` request to the `tax_calculator_url` endpoint, sending the order payload \(including its line items and their items\) in the request body. To trigger the tax update, the order must be not archived and have the following attributes:

* a valid `shipping_address`
* an `external_tax_calculator` associated with the market in scope
* a positive `total_amount_cent`
* at least one SKU among its line item \(gift card are not taxed\)

Your service response \(or error\) must match the format described in the [examples](external-tax-calculators.md#examples) below.

### Taxes data granularity

External taxes can be applied either to the whole order or to specific line items, depending on how granular your response is. If you need to pass tax values at line item level and set tax breakdown attributes, you need to include in the response an array containing the line items you want to be affected by the tax update and specify each line item ID, as the payload passed in the request to your external calculator.

### Values precedence

When designing your external tax calculator response, bear in mind that some values take precedence over other ones, according to the following logic.

#### 1. Line item tax collectable

If the `tax_collectable` attribute is specified for a line item, its value is used to compute the `tax_amount_cents` for the line item, no matter what's the value of the line item `tax_rate` \(if any\).

{% hint style="info" %}
The `tax_collectable` attribute is a `float` \(e.g. `"tax_collectable": 9.0` sets the line item `tax_amount_cents` to 900\).
{% endhint %}

#### 2. Line item tax rate

If the `tax_collectable` is missing for a line item, the line item `tax_amount_cents` is computed using the line item `tax_rate`.

#### 3. Global tax rate

If both the line item `tax_collectable` and `tax_rate` are missing, the line item `tax_amount_cent` is computed using the `tax_rate` specified at the `data` level. If the line items array is missing, that tax rate is applied to the whole order.

### Examples

#### Applying the same tax rate to the whole order

{% tabs %}
{% tab title="Payload" %}
The request payload contains the order and includes its line items and their items:

```javascript
{
  "data": {
    "id": "qLmohvnMrE",
    "type": "orders",
    "links": {...},
    "attributes": {...},
    "relationships": {...},
    "meta": {...}
  },
  "included": [
    {
      "id": "kxnXtEaGxo",
      "type": "line_items",
      "links": {...},
      "attributes": {...},
      "relationships": {...},
      "meta": {...},
    {
      "id": "kXBqtrgARW",
      "type": "line_items",
      "links": {...},
      "attributes": {...},
      "relationships": {...},
      "meta": {...}
    },
    { ... },
    {
      "id": "ZDklSXVMvn",
      "type": "skus",
      "links": {...},
      "attributes": {...},
      "relationships": {...}
      },
      "meta": {...}
    },
    {
      "id": "ZmDzSXLJYn",
      "type": "skus",
      "links": {...},
      "attributes": {...},
      "relationships": {...}
      },
      "meta": {...}
    }
    { ... }
  ]
}
```
{% endtab %}

{% tab title="Response" %}
The successful response must be a JSON object, returning the tax rate to be applied to the whole order, along with some additional information and metadata:

```javascript
{
  "success": true,
  "data": {
    "tax_rate": 0.25,
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

#### Applying different tax rates for some line items

{% tabs %}
{% tab title="Payload" %}
The request payload contains the order and includes its line items and their items:

```javascript
{
  "data": {
    "id": "qLmohvnMrE",
    "type": "orders",
    "links": {...},
    "attributes": {...},
    "relationships": {...},
    "meta": {...}
  },
  "included": [
    {
      "id": "kxnXtEaGxo",
      "type": "line_items",
      "links": {...},
      "attributes": {...},
      "relationships": {...},
      "meta": {...},
    {
      "id": "kXBqtrgARW",
      "type": "line_items",
      "links": {...},
      "attributes": {...},
      "relationships": {...},
      "meta": {...}
    },
    { ... },
    {
      "id": "ZDklSXVMvn",
      "type": "skus",
      "links": {...},
      "attributes": {...},
      "relationships": {...}
      },
      "meta": {...}
    },
    {
      "id": "ZmDzSXLJYn",
      "type": "skus",
      "links": {...},
      "attributes": {...},
      "relationships": {...}
      },
      "meta": {...}
    }
    { ... }
  ]
}
```
{% endtab %}

{% tab title="Response" %}
The successful response must be a JSON object, returning the tax rate to be applied to the line items, along with some additional information and metadata:

```javascript
{
  "success": true,
  "data": {
    "tax_rate": 0.25,
    "line_items": [
      {
        "id": "kxnXtEaGxo",
        "tax_rate": 0.3
      },
      {
        "id": "kXBqtrgARW",
        "tax_rate": 0.4
      }
    ],
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

#### More complex external tax calculation affecting the tax breakdown

{% tabs %}
{% tab title="Payload" %}
The request payload contains the order and includes its line items and their items:

```javascript
{
  "data": {
    "id": "qLmohvnMrE",
    "type": "orders",
    "links": {...},
    "attributes": {...},
    "relationships": {...},
    "meta": {...}
  },
  "included": [
    {
      "id": "kxnXtEaGxo",
      "type": "line_items",
      "links": {...},
      "attributes": {...},
      "relationships": {...},
      "meta": {...},
    {
      "id": "kXBqtrgARW",
      "type": "line_items",
      "links": {...},
      "attributes": {...},
      "relationships": {...},
      "meta": {...}
    },
    { ... },
    {
      "id": "ZDklSXVMvn",
      "type": "skus",
      "links": {...},
      "attributes": {...},
      "relationships": {...}
      },
      "meta": {...}
    },
    {
      "id": "ZmDzSXLJYn",
      "type": "skus",
      "links": {...},
      "attributes": {...},
      "relationships": {...}
      },
      "meta": {...}
    }
    { ... }
  ]
}
```
{% endtab %}

{% tab title="Response" %}
The successful response must be a JSON object, returning all the attribute you want to set through the external service, along with some additional information and metadata:

```javascript
{
  "success": true,
  "data": {
    "freight_taxable": true,
    "tax_rate": 0.25,
    "line_items": [
      {
        "id": "kxnXtEaGxo",
        "tax_collectable": 2.25,
        "country_tax_collectable": 9,
        "country_tax_rate": 0.2,
        "country_taxable_amount": 9,
        "special_tax_rate": 0.05,
        "taxable_amount": 10,
        "tax_rate": 0.4
      },
      {
        "id": "kXBqtrgARW",
        "taxable_amount": 12,
        "tax_rate": 0.3
      }
    ],
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

### Security

When you create a new external tax calculator, a **shared secret** is generated. We recommend verifying the callback authenticity by signing the payload with that shared secret and comparing the result with the callback signature header.

{% page-ref page="../callbacks-security.md" %}

