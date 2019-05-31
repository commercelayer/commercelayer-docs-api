---
description: A comprehensive reference guide to Commerce Layer REST API
---

# Introduction

Commerce Layer exposes a fast [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer) API that lets you add ecommerce to your favorite tech stack. This guide is your reference for all the operations that you can perform on the API resources.

### Base endpoint

All API requests must be made over [HTTPS](http://en.wikipedia.org/wiki/HTTP_Secure) to the following base endpoint:

```text
https://{{subdomain}}.commercelayer.io
```

The `subdomain` parameter is the unique subdomain of your organization. The rest of the documentation omits the base endpoint from all the example requests.

### API Specification

Commerce Layer API is 100% compliant with the [JSON API](http://jsonapi.org/format/) specification \(v1.0\). It supports compound documents, sparse fieldsets, resource linking, filtering, sorting, pagination and more. The JSON API community has shared some [client libraries](http://jsonapi.org/implementations/#client-libraries) that can help you get started. Official libraries and SDKs for the most popular languages are coming soon.

### Applications

Commerce Layer implements the industry-standard [OAuth 2.0](https://oauth.net/2/) protocol to manage clients authorization. It defines four types of applications:

{% tabs %}
{% tab title="Channel" %}
Best suited to create storefront channels, like an ecommerce website or application.
{% endtab %}

{% tab title="Integration" %}
Perfect to integrate any 3rd party system, like an ERP or a CRM, that needs custom permissions.
{% endtab %}

{% tab title="Zapier" %}
Used to authenticate our official [Zapier](https://zapier.com/) app \(currently private\) and to build any workflow.
{% endtab %}

{% tab title="Webapp" %}
Used to authenticate users and access resources on their behalf.
{% endtab %}
{% endtabs %}

Which application to use depends on your specific use case. Official guides and tutorials for the most popular use cases are coming soon.

### Environments

For each organization, you can work either in **test mode** \(default\) or **live mode**. 

Working in test mode is **free forever**. You can try Commerce Layer in test mode as long as you need. Test mode also provides you with a development environment after the go-live. All API calls are identical between the two environments. Use test or live application credentials to make the switch.

