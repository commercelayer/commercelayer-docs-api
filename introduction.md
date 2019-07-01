---
description: How to get your credentials and make the first API call
---

# Getting started

Commerce Layer is free for developers, and it will be forever. So the best way to get started is to [create an account](https://core.commercelayer.io/users/sign_up) and start building.

### 1. Create a test environment

After signup, you are prompted to create a sample organization with test data. This is the fastest way to get your feet wet and start playing with the API in test mode.

![](.gitbook/assets/flat-browser-image-placeholder.jpg)

Your sample organization gets populated with everything you need to place your first test order. Take a look at SKUs, inventory, prices, and settings to get a better idea of how it works.

### 2. Get your credentials

Once your sample organization is ready, go to _Settings → Applications_ and take note of your API credentials.

![](.gitbook/assets/flat-browser-image-placeholder.jpg)

The base endpoint is unique for your organization. The `client_id`, `client_secret`, and `scope` can be used to authenticate your application and get an access token. Public applications can get an access token by using the `client_id` only, with limited permissions. 

{% hint style="info" %}
This is ideal for client side channel applications \(i.e. JavaScript\) that will use our hosted checkout instead of integrating our checkout APIs.
{% endhint %}

### 3. Get an access token

To get an access token for a public **channel** application, run the following in your terminal, making sure to replace your own endpoint and credentials:

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

### 4. Make your first API call

As your first API call, you can get a list of SKUs. Run the following command in your terminal, making sure to replace the access token that you got in the previous step:

```bash
curl -X GET \
    http://yourdomain.commercelayer.io/api/skus \
    -H 'Authorization: Bearer your-access-token' \
    -H 'Content-Type: application/vnd.api+json'
```

The response will look like this:

```javascript
{
  "data": [
    {
      "id": "1234",
      "type": "skus",
      "links": {
        "self": "https://yourdomain.commercelayer.io/api/skus/1234"
      },
      "attributes": {
        "code": "TSHIRTMM000000FFFFFFXLXX",
        "name": "Black Men T-shirt with White Logo (XL)",
        "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        "image_url": "https://img.yourbrand.com/skus/1234.png",
        "tag_names": "Men, Black, XL",
        "pieces_per_pack": "6",
        "weight": "300",
        "unit_of_weight": "gr",
        "id": "1234",
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
            "self": "https://yourdomain.commercelayer.io/api/skus/1234/relationships/shipping_category",
            "related": "https://yourdomain.commercelayer.io/api/skus/1234/shipping_category"
          }
        },
        "prices": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/skus/1234/relationships/prices",
            "related": "https://yourdomain.commercelayer.io/api/skus/1234/prices"
          }
        },
        "stock_items": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/skus/1234/relationships/stock_items",
            "related": "https://yourdomain.commercelayer.io/api/skus/1234/stock_items"
          }
        },
        "delivery_lead_times": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/skus/1234/relationships/delivery_lead_times",
            "related": "https://yourdomain.commercelayer.io/api/skus/1234/delivery_lead_times"
          }
        },
        "sku_options": {
          "links": {
            "self": "https://yourdomain.commercelayer.io/api/skus/1234/relationships/sku_options",
            "related": "https://yourdomain.commercelayer.io/api/skus/1234/sku_options"
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
    "prev": "/api/skus?page[number]=2&page[size]=10",
    "next": "/api/skus?page[number]=4&page[size]=10",
    "last": "/api/skus?page[number]=14&page[size]=10"
  }
}
```

{% hint style="success" %}
Congratulations! 🎉 You just made your first API call, getting a list of SKUs from your account. Now, take the time to explore the rest of the reference, learn more about the available resources and become a pro! 🙌
{% endhint %}

