---
description: How to get your credentials and make the first API call
---

# Getting started

Commerce Layer is free for developers, and it will be forever. So the best way to get started is to [create an account](https://core.commercelayer.io/users/sign_up) and start building.

These are the basic four steps to get started:

1. [Create a test environment](getting-started.md#create-a-test-environment)
2. [Get your credentials](getting-started.md#get-your-credentials)
3. [Get an access token](getting-started.md#get-an-access-token)
4. [Make your first API call](getting-started.md#make-your-first-api-call)

## Create a test environment

After signup, you are prompted to create a sample organization with test data. This is the fastest way to get your feet wet and start playing with the API in test mode.

![](.gitbook/assets/onboarding%20%281%29.jpg)

Your sample organization gets populated with everything you need to place your first test order. Take a look at SKUs, inventory, prices, and settings to get a better idea of how it works.

## Get your credentials

Once your sample organization is ready, go to _Settings → Applications_ and take note of your **sales channel** API credentials.

![](.gitbook/assets/sales-channel%20%282%29.jpg)

The base endpoint is unique for your organization. The `client_id` and `scope` can be used to authenticate your application and get an access token. 

## Get an access token

To get an access token for a **sales channel** application, run the following in your terminal, making sure to replace your own endpoint and credentials:

```bash
curl -X POST \
  https://yourdomain.commercelayer.io/oauth/token \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "grant_type": "client_credentials",
  "client_id": "your-client-id",
  "scope": "market:1234"
}'
```

The response will look like this:

```javascript
{
  "access_token":"your-access-token",
  "token_type":"bearer",
  "expires_in":7200,
  "scope":"market:1234",
  "created_at":1234567890
}
```

Take note of your access token and get ready for your first API call.

{% hint style="warning" %}
Your access token will expire in **2 hours**.
{% endhint %}

## Make your first API call

As your first API call, you can get a list of SKUs. Run the following command in your terminal, making sure to replace the access token that you got in the previous step:

```bash
curl -X GET \
    http://yourdomain.commercelayer.io/api/skus \
    -H 'Accept: application/vnd.api+json' \
    -H 'Authorization: Bearer your-access-token'
```

The response will look like this:

```javascript
{
  "data": [
    {
      "id": "xYZkjABcde",
      "type": "skus",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde"
      },
      "attributes": {
        "code": "TSHIRTMM000000FFFFFFXLXX",
        "name": "Black Men T-shirt with White Logo (XL)",
        "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        "image_url": "https://img.yourbrand.com/skus/xYZkjABcde.png",
        "tag_names": "Men, Black, XL",
        "pieces_per_pack": 6,
        "weight": 300.0,
        "unit_of_weight": "gr",
        "hs_tariff_number": null,
        "do_not_ship": false,
        "do_not_track": false,
        "created_at": "2018-01-01T12:00:00.000Z",
        "updated_at": "2018-01-01T12:00:00.000Z",
        "reference": "ANYREFEFERNCE",
        "metadata": {
          "foo": "bar"
        }
      },
      "relationships": {
        "shipping_category": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/shipping_category",
            "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/shipping_category"
          }
        },
        "prices": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/prices",
            "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/prices"
          }
        },
        "stock_items": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/stock_items",
            "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/stock_items"
          }
        },
        "delivery_lead_times": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/delivery_lead_times",
            "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/delivery_lead_times"
          }
        },
        "sku_options": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/relationships/sku_options",
            "related": "https://yourdomain.commercelayer.io/api/skus/xYZkjABcde/sku_options"
          }
        }
      },
      "meta": {
        "mode": "test"
      }
    },
    {
      "other": "... 9 skus (first page)"
    }
  ],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "/api/skus?page[number]=1&page[size]=10",
    "next": "/api/skus?page[number]=2&page[size]=10",
    "last": "/api/skus?page[number]=14&page[size]=10"
  }
}
```

{% hint style="success" %}
Congratulations! 🎉 You just made your first API call, getting a list of SKUs from your account. Now, take the time to explore the rest of the reference, learn more about the available resources and become a pro! 🙌
{% endhint %}

