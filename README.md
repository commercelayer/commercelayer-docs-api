---
description: A comprehensive reference guide to Commerce Layer REST API
---

# Introduction

Commerce Layer exposes a fast [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer) API that lets you add ecommerce to your favorite tech stack. This guide is your reference for all the operations that you can perform on the API resources.

### Base endpoint

All API requests must be made over [HTTPS](http://en.wikipedia.org/wiki/HTTP_Secure) to the following base endpoint:

```http
https://yourdomain.commercelayer.io
```

Where `yourdomain` is the unique subdomain of your organization. 

### API Specification

Commerce Layer API is 100% compliant with the [JSON API](http://jsonapi.org/format/) specification \(v1.0\). It supports compound documents, sparse fieldsets, resource linking, filtering, sorting, pagination, and more. The JSON API community has shared some [client libraries](http://jsonapi.org/implementations/#client-libraries) that can help you get started.

{% hint style="warning" %}
All the strings passed to the API must be **UTF-8** encoded.
{% endhint %}

Official [JS SDK](https://github.com/commercelayer/commercelayer-js-sdk) and [React components](https://github.com/commercelayer/commercelayer-react-components) are available as open source projects. More libraries and SDKs for the most popular languages are coming soon.

### Applications

Commerce Layer implements the industry-standard [OAuth 2.0](https://oauth.net/2/) protocol to manage clients authorization. It defines three types of applications. Which application to use depends on your specific use case. You can leverage our official [guides and tutorials](https://docs.commercelayer.io/guides/) to get started with the most popular use cases \(more to come\).

### Environments

For each organization, you can work either in **test mode** \(default\) or **live mode**. 

{% hint style="info" %}
Working in test mode is **free forever**. You can try Commerce Layer in test mode as long as you need to.
{% endhint %}

Test mode also provides you with a development environment after the go-live. All API calls are identical between the two environments. Use test or live application credentials to make the switch.

