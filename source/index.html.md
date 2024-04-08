---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - json

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - auth
  - addresses
  - companies
  - contacts
  - customFields
  - deliveryTerms
  - paymentTerms
  - purchaseOrders
  - salesNegotiations
  - salesOrders
  - users

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API
---

# Introduction

WIP version of the Yoda public API documentation. 

# Making a Request

The Yoda API follows a RESTful design.

## Base URL

> URL Structure

```
{environment}.beautynet.co/api/v1/{entity_type}(/{id})
```

> Headers

```json
{
  "Accept": "application/vnd.api+json",
  "Content-Type": "application/api"
}
```

3 environments will be available, however currently only Test is implemented. The base URLs for these environments are:

- Test: `https://apitest.beautynet.co`
- UAT _(TBC)_: `https://apiuat.beautynet.co`
- Production _(TBC)_: `https://api.beautynet.co`

The API is accessed over HTTPS. Once authentication has been successful, all API routes are prefixed with `/api/v1`.
