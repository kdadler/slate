---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
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
  - salesNegotiations
  - users

search: true
---

# Introduction

WIP version of the Yoda public API documentation. 

# Making a Request

The Yoda API follows a RESTful design.

> URL

```
{base_url}/api/v1/{entity_type}(/{id})
```

> Headers

```json
{
  "Accept": "application/vnd.api+json",
  "Content-Type": "application/api"
}
```
