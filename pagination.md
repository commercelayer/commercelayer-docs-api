---
description: How paginated results work
---

# Pagination

When you fetch a collection of resources, you get paginated results. The response contains the record and page counts in the `meta` attribute and the URLs of the other pages in the `links` attribute.

{% hint style="info" %}
The default page number is 1, and the default page size is 10. The maximum page size allowed is 25, but we recommend to use a lower value unless strictly necessary.
{% endhint %}

If you need to modify these default settings, use the `page` query parameter in your request.

### Examples

#### Requesting a specific page

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of SKUs, listed 10 per page \(default\), starting from a specific page:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/skus?page[number]=9 \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
The response contains the record and page counts and the links to the `first`, `prev`, `next` and `last` pages:

```javascript
{
  "data": [...],
  "meta": {
    "record_count": 140,
    "page_count": 14
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/skus?page[number]=1&page[size]=10",
    "prev": "https://yourdomain.commercelayer.io/api/skus?page[number]=8&page[size]=10",
    "next": "https://yourdomain.commercelayer.io/api/skus?page[number]=10&page[size]=10",
    "last": "https://yourdomain.commercelayer.io/api/skus?page[number]=14&page[size]=10"
  }
}
```
{% endtab %}
{% endtabs %}

#### First page

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of SKUs, listed 7 per page, starting from the first page \(default\):

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/skus?page[size]=7 \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
Please note that the link to the `prev` page is now missing:

```javascript
{
  "data": [...],
  "meta": {
    "record_count": 140,
    "page_count": 20
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/skus?page[number]=1&page[size]=7",
    "next": "https://yourdomain.commercelayer.io/api/skus?page[number]=3&page[size]=7",
    "last": "https://yourdomain.commercelayer.io/api/skus?page[number]=20&page[size]=7"
  }
}
```
{% endtab %}
{% endtabs %}

#### Last page

{% tabs %}
{% tab title="Request" %}
The following request fetches a collection of SKUs, listed 5 per page, starting from the last page:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/skus?page[size]=5&page[number]=28 \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
Please note that the link to the `next` page is now missing:

```javascript
{
  "data": [...],
  "meta": {
    "record_count": 140,
    "page_count": 28
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/skus?page[number]=1&page[size]=5",
    "prev": "https://yourdomain.commercelayer.io/api/skus?page[number]=27&page[size]=5",
    "last": "https://yourdomain.commercelayer.io/api/skus?page[number]=28&page[size]=5"
  }
}
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
The example query parameters above use unencoded `[` and `]` characters simply for readability. In practice, these characters must be percent-encoded, per the requirements in [RFC 3986](http://tools.ietf.org/html/rfc3986#section-3.4).
{% endhint %}

