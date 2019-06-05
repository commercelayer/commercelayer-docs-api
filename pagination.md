---
description: How paginated results work
---

# Pagination

When you fetch a collection of resources, you get paginated results. The response contains the record and page counts in the `meta` attribute and the URLs of the other pages in the `links` attribute.

#### Example

```javascript
{
  "data": [...],
  "meta": {
    "record_count": 125,
    "page_count": 5
  },
  "links": {
    "first": "/api/skus?page[number]=1&page[size]=25",
    "prev": "/api/skus?page[number]=2&page[size]=25",
    "next": "/api/skus?page[number]=4&page[size]=25",
    "last": "/api/skus?page[number]=5&page[size]=25"
  }
}
```

{% hint style="warning" %}
The example query parameters above use unencoded \[ and \] characters simply for readability. In practice, these characters must be percent-encoded, per the requirements in [RFC 3986](http://tools.ietf.org/html/rfc3986#section-3.4).
{% endhint %}

{% hint style="info" %}
The default page number is 1, and the default page size is 25. The maximum page size allowed is 100, but we recommend to use a lower value unless strictly necessary.
{% endhint %}

