---
description: The complete list of response codes
---

# Handling errors

Commerce Layer uses [HTTP response codes](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) to show the success or failure of an API request. 

* Codes in the `2xx` range indicate success.
* Codes in the `4xx` range indicate an error that failed given the information provided \(e.g. bad request, failed validation or authentication\).
* Codes in the `5xx` range indicate an unhandled error \(these are rare and should never happen\).

| Code |  | Description |
| :--- | :--- | :--- |
| **`200`** | `OK` | The request was successfully processed and everything worked as expected. |
| **`201`** | `Created` | The request was successfully processed and a new resource was created. |
| **`400`** | `Bad request` | The request was unacceptable, often due to sending an unsupported parameter \([see example](handling-errors.md)\). |
| **`401`** | `Unauthorized` | The access token was not present in the request, was expired or didn't have enough permissions. |
| **`404`** | `Not found` | The requested resource was not found, often due to a wrong resource's ID \([see example](handling-errors.md#404-not-found)\). |
| **`405`** | `Method not allowed` | The request method is known by the server but has been disabled and cannot be used. |
| **`406`** | `Not acceptable` | The **Accept** header was not correctly set to `application/vnd.api+json` |
| **`415`** | `Unsupported media type` | The **Content-type** header was not correctly set to `application/vnd.api+json` |
| **`422`**  | `Unprocessable entity` | The request body was well-formed but contains semantical errors, often due to validation constraints \([see example](handling-errors.md#422-unprocessable-entity)\). |
| **`423`** | `Locked` | The resource could not be deleted due to integrity constraints. |
| **`429`** | `Too many requests` | The request was not accepted because you hit the rate limit \(600 reqs / 5 mins\). |
| **`500`** | `Internal server error` | Something went wrong on our end and is being investigated by our engineers. |

### The error object

All the `4xx` responses include an error object in the response body. The object contains the list of `errors` with extra information. 

{% hint style="warning" %}
A correct error handling is important. We recommend writing code that gracefully handles all possible API exceptions.
{% endhint %}

### Examples

#### 422 Unprocessable Entity

{% tabs %}
{% tab title="Request" %}
The following request tries to update the quantity of a line item with an out-of-range value:

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/line_items/1234 \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -d '{
  "data": {
    "type": "line_items",
    "id": 1234,
    "attributes": {
      "quantity": 100
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
The API responds with a `422 Unprocessable Entity` status code and returns a `VALIDATION_ERROR`:

```javascript
{
  "errors": [
    {
      "title": "must be less than or equal to 10",
      "detail": "quantity - must be less than or equal to 10",
      "code": "VALIDATION_ERROR",
      "source": {
        "pointer": "/data/attributes/quantity"
      },
      "status"=>"422",
      "meta": {
        "error": "less_than_or_equal_to",
        "value": 100,
        "count": 10
      }
    }
  ]
}
```
{% endtab %}
{% endtabs %}

#### 400 Bad Request

{% tabs %}
{% tab title="Request" %}
The following request tries to update a price but the ID in the url does not match with the one in the body:

```javascript
curl -X PATCH \
  https://yourdomain.commercelayer.io/api/prices/1234 \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token' \
  -d '{
  "data": {
    "type": "prices",
    "id": 4321,
    "attributes": {
      "amount_cents": 4900
    }
  }
}'
```
{% endtab %}

{% tab title="Response" %}
The API responds with a `400 Bad Request` status code and returns a `KEY_NOT_INCLUDED_IN_URL` error:

```javascript
{
  "errors": [
    {
      "title": "Key is not included in URL",
      "detail": "The URL does not support the key 10272",
      "code": "KEY_NOT_INCLUDED_IN_URL",
      "status": "400"
    }
  ]
}
```
{% endtab %}
{% endtabs %}

#### 404 Not Found

{% tabs %}
{% tab title="Request" %}
The following request tries to fetch a non existing SKU:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/skus/XXXX \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
The API responds with a `404 Not Found` status code and returns a `RECORD_NOT_FOUND` error:

```javascript
{
  "errors": [
    {
      "title": "Record not found",
      "detail": "The requested resource was not found. Please double-check the resource id.",
      "code": "RECORD_NOT_FOUND",
      "status": "404"
    }
  ]
}
```
{% endtab %}
{% endtabs %}

