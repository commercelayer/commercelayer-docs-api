---
description: How to bulk import resources and their relationships
---

# Importing resources

Commerce Layer lets you import multiple resources in batches. To do that, you need to create a new `import` resource, specify the `resource_type` you want to import, and populate the `inputs` attribute with a JSON list of items. Each element of the `inputs` array contains the resource attributes and relationships.

{% page-ref page="resources/imports/create\_import.md" %}

The process is **asynchronous** and you can poll its `status` attribute to [check the import progress](importing-resources.md#checking-the-import-status). At the end of the import the `processed_count` attribute will indicate the number of imported items. In case of [validation errors](importing-resources.md#handling-import-errors), the `errors_count` and `errors_log`attributes are populated.

{% hint style="info" %}
Resource relationships can be specified by using their IDs. To to that you need to append the `_id` suffix to the name of the related resource \(e.g. `price_list_id`\). Some relationships can also be specified as a nested array of objects \(e.g. order line items\).
{% endhint %}

### Import limits

#### Maximum import size

Imports are subject to some soft limits: the `inputs` array must contain a maximum of **2000** items, otherwise the import will be rejected at creation time. 

#### Maximum error percentage

During the importing phase, the errors count is also monitored: imports whom `errors_count` attribute overflows the maximum percentage of **10%** of the total import size \(i.e. the numbers of items contained in the `inputs` array\) will be interrupted.

### Supported resources

At moment, imports are available for the following resources \(more to come\):

* [Orders](importing-resources.md#importing-a-list-of-orders)
* [Coupons](importing-resources.md#importing-a-list-of-coupons)
* [SKUs](importing-resources.md#importing-a-list-of-skus)
* [Prices](importing-resources.md#importing-a-list-of-prices)
* [Stock items](importing-resources.md#importing-a-list-of-stock-items)
* [Gift cards](importing-resources.md#importing-a-list-of-gift-cards)
* [Customers](importing-resources.md#importing-a-list-of-customers)
* [Customer subscriptions](importing-resources.md#importing-a-list-of-customer-subscriptions)
* [Tax categories](importing-resources.md#importing-a-list-of-tax-categories)

### Unique keys

{% hint style="info" %}
If the single resource to be imported doesn't exist it gets created, otherwise it is updated. 
{% endhint %}

In order to detect if a resource already exists the `id` key is checked for each `inputs` entry. Some resources also support specific \(combined\) attributes to identify an existing record, which can be helpful in case the resource ID isn't known during the import phase:

* Orders — `number`
* Coupons — `code` + `promotion_rule_id`
* SKUs — `code`
* Prices — `sku_code` + `price_list_id`
* Stock items —  `sku_code` + `stock_location_id`
* Gift cards — `code`
* Customers — `email`
* Customer subscriptions — `customer_id` + `reference`
* Tax categories — `code` + `tax_calculator_id`

### Specifying the parent resource

If the resources you're importing refers to the same parent resource \(e.g. prices to the same price list\), you can avoid repeating its value on each inputs items by specifying the `parent_resource_id` attribute. In case you specify both the parent resource ID and the relationship ID for each item, the latter wins. These are the supported parent resources:

* Orders — `market_id`
* Coupons — `promotion_rule_id`
* Prices — `price_list_id`
* Stock items —  `stock_location_id`
* Gift cards — `market_id`
* Tax categories — `tax_calculator_id`

### Cleaning up records

Set the `cleanup_records` attribute as `true` if you want all the resources that are not present in the `inputs` list to be deleted at the end of the import. You can monitor the number of destroyed records once the import has completed by inspecting the `destroyed_count` attribute.

{% hint style="warning" %}
Be careful when cleaning up records — **this action is not reversible**. The `cleanup_records` flag is better used in combination with the `parent_resource_id` attribute in order to reduce the scope of the destroyed records. If the parent resource ID is missing all of the not-imported resources for the organization will be affected by the cleanup, which might not be what you want.
{% endhint %}

### Examples

#### Importing a list of orders

{% tabs %}
{% tab title="Request" %}
The following request creates an import with a list of orders with associated line items and archives them at the same time:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/imports \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
	"data": { 
	  "type": "orders",
	  "attributes": {
	    "resource_type": "orders",
	    "parent_resource_id": "KmjljGJzWQ"
	    "inputs": [
	      {
	        "customer_email": "john@example.com",
	        "_archive": 1,               
	        "line_items": [
	          {
	            "item_type": "sku",
	            "name": "BABYONBU000000E63E7424MX",
	            "quantity": 2,
	            "unit_amount_cents": 1000
	           },
	           { 
	             "item_type": "sku",
	             "name": "BABYONBU000000E63E7418MX",
	             "quantity": 1,
	             "unit_amount_cents": 2000
	            }
	        ]
	      },
	      {
	        "customer_email": "jack@example.com",
	        "_archive": 1,
	        "line_items": [
	          { 
	             "item_type": "sku",
	             "name": "BABYONBU000000E63E7667MX",
	             "quantity": 2,
	             "unit_amount_cents": 1500
	            }
	        ]
	      },
        {...}
      ]
	  }
	}
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created import object with its status set to `pending`:

```javascript
{
  "data": {
    "id": "PmjlkIJzRA",
    "type": "imports",
    "links": {...},
    "attributes": {
      "resource_type": "orders",
      "parent_resource_id": "KmjljGJzWQ",
      "status": "pending",
      "started_at": null,
      "completed_at": null,
      "interrupted_at": null,
      "inputs": [...],
      "inputs_size": 100,
      "errors_count": 0,
      "warnings_count": 0,
      "destroyed_count": 0,
      "processed_count": 0,
      "errors_log": {},
      "warnings_log": {},
      "cleanup_records": false,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": null,
      "reference_origin": null,
      "metadata": {}
    },
    "meta": {
      "mode": "test"
    }
  }

```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
To create an import of orders for the same **market**, remember to specify its ID as the `parent_resource_id` attribute.
{% endhint %}

For a list of all the required attributes you need to create an order, refer to the related section of this API reference:

{% page-ref page="resources/orders/create\_order.md" %}

#### Importing a list of coupons

{% tabs %}
{% tab title="Request" %}
The following request creates an import with a list of coupons and cleanup the ones existing for the same promotion rule:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/imports \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
	"data": {
	  "type": "imports",
	  "attributes": {
	    "resource_type": "coupons",
	    "parent_resource_id": "FreQKlNxZA"
	    "cleanup_records": "true",
	    "inputs": [
	      {
	        "code": "XXXXXXXX",
	        "usage_limit": 10
	      },
	      {
	        "code": "YYYYYYYY",
	        "usage_limit": 5
	      },
        {...}
      ]
	  }
	}
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created import object with its status set to `pending`:

```javascript
{
  "data": {
    "id": "PmjlkIJzRA",
    "type": "imports",
    "links": {...},
    "attributes": {
      "resource_type": "coupons",
      "parent_resource_id": "FreQKlNxZA",
      "status": "pending",
      "started_at": null,
      "completed_at": null,
      "interrupted_at": null,
      "inputs": [...],
      "inputs_size": 100,
      "errors_count": 0,
      "warnings_count": 0,
      "destroyed_count": 0,
      "processed_count": 0,
      "cleanup_records": true,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": null,
      "reference_origin": null,
      "metadata": {}
    },
    "meta": {
      "mode": "test"
    }
  }
}
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
Please note that in this case — since the `cleanup_records` attribute is set as `true` — all of the coupons for the specified promotion rule that aren't included in the `inputs` list will be destroyed.
{% endhint %}

For a list of all the required attributes you need to create a coupon, refer to the related section of this API reference:

{% page-ref page="resources/coupons/create\_coupon.md" %}

#### Importing a list of SKUs

{% tabs %}
{% tab title="Request" %}
The following request creates an import with a list of SKUs:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/imports \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
	"data": {
	  "type": "imports",
	  "attributes": {
	    "resource_type": "skus",
	    "inputs": [
	      {
	    	  "code":"BABYONBU000000E63E7424MX",
	    	  "name":"Black Baby Onesie Short Sleeve with Pink Logo (24 Months)",
	    	  "image_url":"https://img.yourdomain.com/skus/BABYONBU000000E63E74.png",
	    	  "reference": "BABYONBU000000E63E74",
	    	  "shipping_category_id": "zwzQeFBrNj"
	      },
	      {
	    	  "code":"BABYONBU000000E63E7418MX",
	    	  "name":"Black Baby Onesie Short Sleeve with Pink Logo (18 Months)",
	    	  "image_url":"https://img.yourdomain.com/skus/BABYONBU000000E63E74.png",
	    	  "reference": "BABYONBU000000E63E74",
	    	  "shipping_category_id": "zwzQeFBrNj"
	      },
        {...}
      ]
	  }
	}
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created import object with its status set to `pending`:

```javascript
{
  "data": {
    "id": "PmjlkIJzRA",
    "type": "imports",
    "links": {...},
    "attributes": {
      "resource_type": "skus",
      "parent_resource_id": null,
      "status": "pending",
      "started_at": null,
      "completed_at": null,
      "interrupted_at": null,
      "inputs": [...],
      "inputs_size": 100,
      "errors_count": 0,
      "warnings_count": 0,
      "destroyed_count": 0,
      "processed_count": 0,
      "cleanup_records": false,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": null,
      "reference_origin": null,
      "metadata": {}
    },
    "meta": {
      "mode": "test"
    }
  }
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Specifying the `shipping_category_id` attribute for each single item of the `inputs` array lets you import SKUs associated with different shipping categories all at once.
{% endhint %}

For a list of all the required attributes you need to create an SKU, refer to the related section of this API reference:

{% page-ref page="resources/skus/create\_sku.md" %}

#### Importing a list of prices

{% tabs %}
{% tab title="Request" %}
The following request creates an import with a list of prices:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/imports \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
	"data": {
	  "type": "imports",
	  "attributes": {
	    "resource_type": "prices",
	    "parent_resource_id": "vLrWRCJWBE",
	    "inputs": [
	      {
	        "sku_code": "BABYONBU000000E63E7424MX",
	        "amount_cents": 3990,
	        "compare_at_amount_cents": 5000
	      },
	      {
	        "sku_code": "BABYONBU000000E63E7418MX",
	        "amount_cents": 3490,
	        "compare_at_amount_cents": 4700
	      },
        {...}
      ]
	  }
	}
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created import object with its status set to `pending`:

```javascript
{
  "data": {
    "id": "ZbDQzIoxnA",
    "type": "imports",
    "links": {...},
    "attributes": {
      "resource_type": "prices",
      "parent_resource_id": "vLrWRCJWBE",
      "status": "pending",
      "started_at": null,
      "completed_at": null,
      "interrupted_at": null,
      "inputs": [...],
      "inputs_size": 100,
      "errors_count": 0,
      "warnings_count": 0,
      "destroyed_count": 0,
      "processed_count": 0,
      "cleanup_records": false,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": null,
      "reference_origin": null,
      "metadata": {}
    },
    "meta": {
      "mode": "test"
    }
  }
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
To create an import of prices for the same **price list**, remember to specify its ID as the `parent_resource_id` attribute.
{% endhint %}

For a list of all the required attributes you need to create a price, refer to the related section of this API reference:

{% page-ref page="resources/prices/create\_price.md" %}

#### Importing a list of stock items

{% tabs %}
{% tab title="Request" %}
The following request creates an import with a list of stock items:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/imports \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
	"data": {
	  "type": "imports",
	  "attributes": {
	    "resource_type": "stock_items",
	    "parent_resource_id": "bnEeQuqZgn",
	    "inputs": [
	      {
	        "sku_code": "BABYONBU000000E63E7424MX",
	        "quantity": 110
	      },
	      {
	        "sku_code": "BABYONBU000000E63E7418MX",
	        "quantity": 140
	      },
        {...}
	    ]
	  }
	}
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created import object with its status set to `pending`:

```javascript
{
  "data": {
    "id": "YqQJGIYWjm",
    "type": "imports",
    "links": {...},
    "attributes": {
      "resource_type": "stock_items",
      "parent_resource_id": "bnEeQuqZgn",
      "status": "pending",
      "started_at": null,
      "completed_at": null,
      "interrupted_at": null,
      "inputs": [...],
      "inputs_size": 100,
      "errors_count": 0,
      "warnings_count": 0,
      "destroyed_count": 0,
      "processed_count": 0,
      "cleanup_records": false,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": null,
      "reference_origin": null,
      "metadata": {}
    },
    "meta": {
      "mode": "test"
    }
  }
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
To create an import of stock items for the same **stock location**, remember to specify its ID as the `parent_resource_id` attribute.
{% endhint %}

For a list of all the required attributes you need to create a stock item, refer to the related section of this API reference:

{% page-ref page="resources/stock\_items/create\_stock\_item.md" %}

#### Importing a list of gift cards

{% tabs %}
{% tab title="Request" %}
The following request creates an import with a list of gift cards:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/imports \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
	"data": {
	  "type": "imports",
	  "attributes": {
	    "resource_type": "gift_cards",
	    "parent_resource_id": "bgOEQhznoZ",
	    "inputs": [
        {
	     	  "balance_cents": 12500,
        	"currency_code": "USD",
        	"single_use": false,
        	"rechargeable": true,
        	"image_url": "https://img.yourdomain.com/skus/MYGITFCARDIMAGE.png",
        	"expires_at": "2030-01-01T00:00:00Z",
			    "recipient_email": "john@example.com"
	      },
	      {
	     	  "balance_cents": 20000,
        	"currency_code": "EUR",
        	"single_use": true,
        	"rechargeable": false,
        	"expires_at": "2025-01-01T00:00:00Z",
			    "recipient_email": "jane@example.com"
	      },
	      {...}
	    ]
	  }
	}
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created import object with its status set to `pending`:

```javascript
{
  "data": {
    "id": "BAzkwIRNkq",
    "type": "imports",
    "links": {...},
    "attributes": {
      "resource_type": "gift_cards",
      "parent_resource_id": "bgOEQhznoZ",
      "status": "pending",
      "started_at": null,
      "completed_at": null,
      "interrupted_at": null,
      "inputs": [...],
      "inputs_size": 100,
      "errors_count": 0,
      "warnings_count": 0,
      "destroyed_count": 0,
      "processed_count": 0,
      "errors_log": {},
      "warnings_log": {},
      "cleanup_records": false,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": null,
      "reference_origin": null,
      "metadata": {}
    },
    "meta": {
      "mode": "test"
    }
  }
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
To create an import of gift cards for the same **market**, remember to specify its ID as the`parent_resource_id` attribute.
{% endhint %}

For a list of all the required attributes you need to create a gift card, refer to the related section of this API reference:

{% page-ref page="resources/gift\_cards/create\_gift\_card.md" %}

#### Importing a list of customers

{% tabs %}
{% tab title="Request" %}
The following request creates an import with a list of customers:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/imports \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
	"data": {
	  "type": "imports",
	  "attributes": {
	    "resource_type": "customers",
	    "inputs": [
	      {
	        "email": "john@example.com"
	      },
	      {
	        "email": "jack@example.com",
	        "password": "secret",
	        "customer_group_id": "KngqdhAlpd"
	      },
        {...}
	    ]
	  }
	}
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created import object with its status set to `pending`:

```javascript
{
  "data": {
    "id": "ZqDQzIoznm",
    "type": "imports",
    "links": {...},
    "attributes": {
      "resource_type": "customers",
      "parent_resource_id": null,
      "status": "pending",
      "started_at": null,
      "completed_at": null,
      "interrupted_at": null,
      "inputs": [...],
      "inputs_size": 100,
      "errors_count": 0,
      "warnings_count": 0,
      "destroyed_count": 0,
      "processed_count": 0,
      "errors_log": {},
      "warnings_log": {},
      "cleanup_records": false,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": null,
      "reference_origin": null,
      "metadata": {}
    },
    "meta": {
      "mode": "test"
    }
  }
}
```
{% endtab %}
{% endtabs %}

For a list of all the required attributes you need to create a customer, refer to the related section of this API reference:

{% page-ref page="resources/customers/create\_customer.md" %}

#### Importing a list of customer subscriptions

{% tabs %}
{% tab title="Request" %}
The following request creates an import with a list of customer subscriptions:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/imports \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
	"data": {
	  "type": "imports",
	  "attributes": {
	    "resource_type": "customer_subscriptions",
	    "inputs": [
        {
  	      "customer_email": "john@example.com",
  	      "reference": "Marketing newsletter"
  	    },
  	    {
  	      "customer_email": "jane@example.com",
  	      "reference": "Whitepaper download"
  	    },
        {...}
	    ]
	  }
	}
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created import object with its status set to `pending`:

```javascript
{
  "data": {
    "id": "NqYzgIKvdm",
    "type": "imports",
    "links": {...},
    "attributes": {
      "resource_type": "customer_subscriptions",
      "parent_resource_id": null,
      "status": "pending",
      "started_at": null,
      "completed_at": null,
      "interrupted_at": null,
      "inputs": [...],
      "inputs_size": 100,
      "errors_count": 0,
      "warnings_count": 0,
      "destroyed_count": 0,
      "processed_count": 0,
      "errors_log": {},
      "warnings_log": {},
      "cleanup_records": false,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": null,
      "reference_origin": null,
      "metadata": {}
    },
    "meta": {
      "mode": "test"
    }
  }
}
```
{% endtab %}
{% endtabs %}

For a list of all the required attributes you need to create a customer subscription, refer to the related section of this API reference:

{% page-ref page="resources/customer\_subscriptions/create\_customer\_subscription.md" %}

#### Importing a list of tax categories

{% tabs %}
{% tab title="Request" %}
The following request creates an import with a list of tax categories:

```javascript
curl -X POST \
  https://yourdomain.commercelayer.io/api/imports \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
	"data": {
	  "type": "imports",
	  "attributes": {
	    "resource_type": "tax_categories",
	    "parent_resource_id": "daSWQhzjkiZ",
	    "inputs": [
        {
          "sku_code": "BABYONBU000000E63E7424MX",
          "code": "31000",
        },
        {
          "sku_code": "BABYONBU000000E63E7418MX",
          "code": "31000",
        },
        {...}
	    ]
	  }
	}
}'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `201 Created` status code, returning the created import object with its status set to `pending`:

```javascript
{
  "data": {
    "id": "NqYzgIKvdm",
    "type": "imports",
    "links": {...},
    "attributes": {
      "resource_type": "tax_categories",
      "parent_resource_id": "daSWQhzjkiZ",
      "status": "pending",
      "started_at": null,
      "completed_at": null,
      "interrupted_at": null,
      "inputs": [...],
      "inputs_size": 100,
      "errors_count": 0,
      "warnings_count": 0,
      "destroyed_count": 0,
      "processed_count": 0,
      "errors_log": {},
      "warnings_log": {},
      "cleanup_records": false,
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": null,
      "reference_origin": null,
      "metadata": {}
    },
    "meta": {
      "mode": "test"
    }
  }
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
To create an import of tax categories for the same **promotion rule**, remember to specify its ID as the`parent_resource_id` attribute.
{% endhint %}

For a list of all the required attributes you need to create a tax category, refer to the related section of this API reference:

{% page-ref page="resources/tax\_categories/create\_tax\_category.md" %}

### Checking the import status

You can inspect the status of a specific import by fetching the single import by ID and looking at the `status` attribute.

{% tabs %}
{% tab title="Request" %}
The following request fetches a single import, the one identified by the ID "PmjlkIJzRA":

```javascript
curl -X GET \ 
  https://yourdomain.commercelayer.io/api/imports/PmjlkIJzRA \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning the single import object:

```javascript
{
  "data": {
    "id": "PmjlkIJzRA",
    "type": "imports",
    "links": {...},
    "attributes": {
      "resource_type": "skus",
      "parent_resource_id": null,
      "status": "completed",
      "started_at": "2018-01-01T12:00:00.000Z",
      "completed_at": "2018-01-01T12:01:00.000Z",
      "interrupted_at": null,
      "inputs": [...],
      "inputs_size": 100,
      "errors_count": 5,
      "warnings_count": 0,
      "destroyed_count": 0,
      "processed_count": 95,
      "errors_log": {...},
      "warnings_log": {},
      "cleanup_records": "false",
      "created_at": "2018-01-01T12:00:00.000Z",
      "updated_at": "2018-01-01T12:00:00.000Z",
      "reference": null,
      "reference_origin": null,
      "metadata": {}
    },
    "meta": {
      "mode": "test"
    }
  }
}
```
{% endtab %}
{% endtabs %}

You can also leverage Commerce Layer real-time webhooks mechanism, listen to `imports.create`, `imports.start`, `imports.complete`, `imports.interrupt`, or `imports.destroy` and react properly.

{% page-ref page="real-time-webhooks.md" %}

### Handling import errors

When an import is completed or interrupted, import errors and warnings \(related to [cleanup](importing-resources.md#cleaning-up-records)\) are reported through the `errors_count`, `errors_log`, `warnings_count`, and `warnings_log` attributes:

```javascript
...

"errors_count": 5,
"warnings_count": 0,
"destroyed_count": 0,
"processed_count": 95,
"errors_log": {
  "BABYONBU000000E63E7418MX": {
    "name": [
      "has already been taken"
    ]
  },
  "BABYONBU000000E63E7424MX": {
    "shipping_category": [
      "must exist"
    ]
  },
  ...
},
"warnings_log": {},

...
```

{% hint style="info" %}
In case you need to know at which point an import has been interrupted, you simply can sum the `processed_count` and the `errors_count` attributes: the result will be the index of the last `inputs` item that caused the interruption.
{% endhint %}

