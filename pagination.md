---
description: How paginated results work
---

# Pagination

When you fetch a collection of resources, you get paginated results. The response contains the record and page counts in the `meta` attribute and the URLs of the other pages in the `links` attribute.

{% hint style="info" %}
The default page number is 1, and the default page size is 10. The maximum page size allowed is 25, but we recommend to use a lower value unless strictly necessary.
{% endhint %}

If you need to modify these default settings, use the `page` query parameter in your request.

### Example

{% tabs %}
{% tab title="Request" %}
The following request fetches the SKUs, setting the page number to 3 and the page size to 5:

```javascript
curl -X GET \
  https://yourdomain.commercelayer.io/api/skus?page[size]=5&page[number]=3 \
  -H 'Accept: application/vnd.api+json' \
  -H 'Authorization: Bearer your-access-token'
```
{% endtab %}

{% tab title="Response" %}
On success, the API responds with a `200 OK` status code, returning the five resource objects listed in the third page \(from the 6th object to the 10th\), together with the record and page counts and the links to the `first`, `prev`, `next` and `last` page.

```javascript
{
  "data": [...],
  "meta": {
    "record_count": 140,
    "page_count": 28
  },
  "links": {
    "first": "https://yourdomain.commercelayer.io/api/skus?page[number]=1&page[size]=5",
    "prev": "https://yourdomain.commercelayer.io/api/skus?page[number]=2&page[size]=5",
    "next": "https://yourdomain.commercelayer.io/api/skus?page[number]=4&page[size]=5",
    "last": "https://yourdomain.commercelayer.io/api/skus?page[number]=28&page[size]=5"
  }
}
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
The example query parameters above use unencoded `[` and `]` characters simply for readability. In practice, these characters must be percent-encoded, per the requirements in [RFC 3986](http://tools.ietf.org/html/rfc3986#section-3.4).
{% endhint %}

